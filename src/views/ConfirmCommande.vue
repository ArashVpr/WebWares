<template>
  <div class="container">
    <div v-if="commandeProduits.length">
      <h2>Détails de la commande</h2>

      <div>
        <h3>Produits dans la commande :</h3>
        <ul>
          <li v-for="(produit, index) in commandeProduits" :key="index">
            {{ produit.titre }} (x{{ produit.quantite }})
          </li>
        </ul>
        <p>
          Montant total à payer :
          <br />
          <strong>{{ totalHT }} € (HT)</strong>
          <br />
          <strong>{{ total }} € (TTC)</strong>
        </p>
      </div>

      <div v-if="utilisateur">
        <h3>Coordonnées de réception :</h3>
        <p><strong>Nom :</strong> {{ utilisateur.raisonSociale }}</p>
        <p>
          <strong>Adresse de livraison :</strong>
          <br />
          {{ utilisateur.adresse }},
          <br />
          {{ utilisateur.codePostal }}
          {{ utilisateur.ville }}
        </p>
      </div>
      <div>
        <h3>Information complémentaire :</h3>
        <textarea
          v-model="informationComplementaire"
          placeholder="Ajouter votre message ou information ici..."
          rows="10"
          cols="35"
        ></textarea>
      </div>
      <br />
      <ButtonComponents
        label="Valider la commande"
        type="submit"
        @click="openValidateCommandeModal"
      />
    </div>

    <div v-else>
      <p><strong>Commande en cours de traitement!</strong></p>
      <br />
      <ButtonComponents
        label="Retour Accueil"
        type="login"
        @click="$router.push('/')"
      />
    </div>

    <ModalComponent :showModal="showModalCommandeConfirm" color="#d7c3a7">
      <template #header>
        <h2>Confirmation de la commande :</h2>
      </template>

      <template #body>
        <p>Êtes-vous sûr de vouloir valider votre commande?</p>
      </template>

      <template #footer>
        <div class="btn-conf">
          <ButtonComponents
            label="Valider"
            type="login"
            @click="validerCommande()"
          />
          <ButtonComponents
            label="Annuler"
            type="logout"
            @click="closeValidateCommandeModal"
          />
        </div>
      </template>
    </ModalComponent>
  </div>
</template>

<script>
import ButtonComponents from "@/components/ButtonComponents.vue";
import ModalComponent from "@/components/ModalComponent.vue";
import { mapState, mapGetters } from "vuex";

export default {
  components: {
    ButtonComponents,
    ModalComponent,
  },
  data() {
    return {
      showModalCommandeConfirm: false,
    };
  },
  computed: {
    // ...mapState(["commandes", "utilisateurs"]),
    // --- ici j'ai juste remplacé utilisateur  par currentUtilisateur afin de suivre la connexion de l'utilisateur, ce qui nous permet de set la confirmation de ses
    // commandes sur son id et ses datas correspondantes
    ...mapState(["commandes", "utilisateurs", "currentUtilisateur"]),

    //    ...mapGetters(["total"]),

    ...mapGetters(["total", "totalHT"]),

    commandeProduits() {
      return this.commandes.flatMap((commande) => commande.produits);
    },

    utilisateur() {
      // return this.utilisateurs.find((user) => user.id === 1);
      // return this.currentUtilisateur;
      const currentUser = this.currentUtilisateur;
      if (!currentUser) return null;
      return this.utilisateurs.find((user) => user.id === currentUser.id);
    },
  },
  methods: {
    openValidateCommandeModal() {
      this.showModalCommandeConfirm = true;
    },
    closeValidateCommandeModal() {
      this.showModalCommandeConfirm = false;
      this.commandeValidated = null;
    },

    validerCommande() {
      const currentCommande = {
        produits: this.commandeProduits,
        countTotalHT: this.totalHT,
        countTotalTTC: this.total,
        userId: 1,
        commentaire: this.informationComplementaire,
      };

      this.$store.commit("saveCommandeToLocalStorage", currentCommande);
      this.$store.commit("clearPanier");
      this.closeValidateCommandeModal();
      // --- ici je nettoyerais les saved commandes correspondant à l'id de l'utilisateur
      this.$store.dispatch("clearSavedCommandesForUser");
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 30px;
}

.btn-conf {
  display: flex;
  justify-content: center;
  gap: 15px;
}
</style>
