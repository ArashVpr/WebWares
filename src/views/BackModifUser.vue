<template>
    <div class="add">
        <p>Modifier un User</p>
            <form>
                <label for="raisonSociale">Nom entreprise:</label><br>
                <input type="text" id="raisonSociale" name="raisonSociale" v-model="editUser.raisonSociale"><br>

                <label for="siret">Numéro SIRET:</label><br>
                <input type="text" id="siret" name="siret" v-model="editUser.siret"><br>

                <label for="adresse">Adresse:</label><br>
                <input type="text" id="adresse" name="adresse" v-model="editUser.adresse"><br>

                <label for="codePostal">Code Postal:</label><br>
                <input type="text" id="codePostal" name="codePostal" v-model="editUser.codePostal"><br>

                <label for="ville">Ville:</label><br>
                <input type="text" id="ville" name="ville" v-model="editUser.ville"><br>

                <label for="email">Email:</label><br>
                <input type="text" id="email" name="email" v-model="editUser.email"><br>

                <label for="motDePasse">Mot de Passe:</label><br>
                <input type="text" id="motDePasse" name="motDePasse" v-model="editUser.motDePasse"><br>
                
                <label for="role">Rôle:</label><br>
                <select id="role" name="role" v-model="editUser.role">
                    <option value="USER">Utilisateur</option>
                    <option value="ADMIN">Administrateur</option>

                </select><br>
                <br>
                <div class="boutons">
                  <ButtonComponents label="Modifier" type="login" @click.prevent="modUser()" style="margin-right: 0.5rem"></ButtonComponents>
                  <ButtonComponents label="Annuler" type="logout" @click.prevent="goBack()"></ButtonComponents>
                </div>
            </form>
            <ModalComponent :showModal="showModalConfirm" color="#d7c3a7">
            <template #header>
              <h2>Veuillez remplir tous les champs</h2>
            </template>

            <template #body>
              <p></p>
            </template>
            <template #footer>
          <ButtonComponents
            label="Continuer"
            type="submit"
            @click="closeModal()"
          />
        </template>
      </ModalComponent>
    </div>
  </template>
  
  <script>
  import ButtonComponents from "@/components/ButtonComponents.vue";
import ModalComponent from "@/components/ModalComponent.vue";
  import { mapState, mapMutations } from "vuex";


  export default {
    components:{
        ButtonComponents,
        ModalComponent
    },
    data() {
    return {
      editUser: {
        raisonSociale: "",
        siret: "",
        adresse: "",
        codePostal: "",
        ville: "",
        email: "",
        motDePasse: "",
        role: "",
      },
      payload: {key1: {}, key2: (this.$route.params.id)},
      showModalConfirm: false,

    };
    },
    methods: {
    ...mapMutations(['backModUser']),
    modUser(){
      if (this.editUser.raisonSociale && this.editUser.siret && this.editUser.adresse && this.editUser.codePostal && this.editUser.ville && this.editUser.email && this.editUser.motDePasse && this.editUser.role){
        this.editUser.id = this.$route.params.id
        this.payload.key1 = this.editUser
        this.backModUser(this.payload)
        this.goBack()
        } else {
          this.openModal()
        }
    },
    
    goBack() {
      this.$router.back()
    },
    openModal() {
      this.showModalConfirm = true;
    },
    closeModal() {
      this.showModalConfirm = false;
    },
    },
    computed:{
      ...mapState(["utilisateurs"]),
    },
    mounted() {
    if (this.utilisateurs[this.utilisateurs.map((e) => e.id).indexOf(parseInt(this.$route.params.id))]) {
      this.editUser = { ...this.utilisateurs[this.utilisateurs.map((e) => e.id).indexOf(parseInt(this.$route.params.id))] };
    }
  },
    }
  </script>
  
  <style scoped>
    .add {
    display: flex;
    flex-direction: column;
    align-self: center;
    background-color: wheat;
    padding: 20px 60px 20px 60px;
    border-radius: 25px;
    margin: 30px;
  }
  p {
    font-size: 24px;
  }
  .boutons {
    display: flex;
    justify-content: space-around;

  }
  </style>