<template>
  <div>
    <form class="form-horizontal">
      <fieldset>
        <legend>Générez votre signature</legend>
        <div class="form-group">
          <label for="inputFirstName" class="col-lg-2 control-label">Prénom</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputFirstName" placeholder="John" type="text" v-model="inputFirstName" v-on:focus="showName()">
          </div>
        </div>

        <div class="form-group">
          <label for="inputLastName" class="col-lg-2 control-label">Nom</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputLastName" placeholder="Doe" type="text" v-model="inputLastName" v-on:focus="showName()">
          </div>
        </div>

        <div class="form-group">
          <label for="inputEmail" class="col-lg-2 control-label">Email</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputEmail" placeholder="john.doe@team-scylla.fr" type="text" v-model="inputEmail" v-on:focus="showMail()">
          </div>
        </div>

        <div class="form-group">
          <label for="inputPhone" class="col-lg-2 control-label">Téléphone</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputPhone" placeholder="06 00 00 00 00" type="text" v-model="inputPhone" v-on:focus="showPhone()">
          </div>
        </div>

        <div class="form-group">
          <label for="inputRole" class="col-lg-2 control-label">Poste</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputRole" placeholder="Président" type="text" v-model="inputRole" v-on:focus="showRole()">
          </div>
        </div>

        <div class="form-group">
          <label for="inputlinkedIn" class="col-lg-2 control-label">Lien de votre LinkedIn</label>
          <div class="col-lg-10">
            <input class="form-control" id="inputLinkedIn" placeholder="https://linkedin.com/..." type="text" v-model="inputLinkedIn">
          </div>
        </div>
      </fieldset>
    </form>

    <div class="panel panel-default first">
      <div class="panel-heading">Voici votre signature</div>
      <div class="panel-body" id="signature">
        <div style="float: left; margin: 2px 5px 5px 0px; padding-right: 5px; display: block;">
          <img src="https://public.alexandre-martin.fr/BDE/logo.png" width="90px" height="90px">
        </div>
        <div style="margin-top:0px; margin-left: 110px">
          <p style="font-family: Helvetica, sans-serif; font-size: 12px; line-height: 14px; color: #333; margin-top:0; margin-left:0; padding-left:0;">
            <strong>
              <span v-if="displayName">{{ inputFirstName }} {{ inputLastName }}</span>
              <span v-else>John Doe</span>
            </strong>
            <span v-if="displayRole">/ {{ inputRole }} BDE Scylla</span>
            <span v-else>/ Président BDE Scylla</span><br>
            <span v-if="displayMail"> <a v-bind:href="'mailto:' +  inputEmail" style="color:#3684c8;">{{ inputEmail }}</a></span>
            <span v-else><a href="mailto:john.doe@team-scylla.fr" style="color:#3684c8;">john.doe@team-scylla.fr</a></span><br>
            <span v-if="displayPhone">{{ inputPhone }}</span>
            <span v-else>06 00 00 00 00</span>
          </p>
          <p style="font-family: Helvetica, sans-serif; font-size: 12px; line-height: 14px; color: rgb(51, 51, 51); margin-top: 0px;">
            <span style="font-size: 10px; line-height: 14px; margin: 5px 0; display:block; opacity:0.8;"><a v-bind:href="inputLinkedIn" target="_blank" style="color: black">LinkedIn</a></span>
            <span><a href="http://team-scylla.fr" style="color:#3684c8;" rel="nofollow" target="_blank">https://team-scylla.fr</a></span> <br>
          </p>
        </div>
      </div>
    </div>

    <div class="panel panel-default">
      <div class="panel-heading">Code html de votre signature</div>
      <div class="panel-body">
        <div class="panel-body">
          <textarea id="htmlForm"></textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'generator',
    data () {
      return {
        inputFirstName: '',
        inputLastName: '',
        inputRole: '',
        inputEmail: '',
        inputPhone: '',
        inputLinkedIn: 'https://www.linkedin.com/company-beta/10577553/',
        displayName: false,
        displayRole: false,
        displayMail: false,
        displayPhone: false
      }
    },
    methods: {
      showName () {
        this.$data.displayName = true
      },
      showRole () {
        this.$data.displayRole = true
      },
      showMail () {
        this.$data.displayMail = true
      },
      showPhone () {
        this.$data.displayPhone = true
      },
      updateHtml () {
        this.$nextTick(function () {
          window.$('#htmlForm').text(window.$('#signature').html())
        })
      }
    },
    mounted () {
      window.$('#htmlForm').text(window.$('#signature').html())
    },
    watch: {
      inputFirstName: function () { this.updateHtml() },
      inputLastName: function () { this.updateHtml() },
      inputRole: function () { this.updateHtml() },
      inputEmail: function () { this.updateHtml() },
      inputPhone: function () { this.updateHtml() },
      inputLinkedIn: function () { this.updateHtml() }
    }
  }
</script>

<style>
  .panel.first {
    margin-top: 50px;
  }

  textarea {
    width: 100%;
  }
</style>
