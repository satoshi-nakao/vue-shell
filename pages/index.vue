<template>
  <div class="container">
    <div>
      <logo />
      <v-shell
      :banner="banner"
      :shell_input="send_to_terminal"
      :commands="commands"
      @shell_output="prompt"
      ></v-shell>
    </div>
  </div>
</template>
 
<script>
import Logo from '~/components/Logo.vue'
 
export default {
  components: {
    Logo
  },
  data() {
    return {
      send_to_terminal: "",
      banner: {
        header: "Vue Shell",
        subHeader: "Shell is power just enjoy 🔥",
        helpHeader: 'Enter "help" for more information.',
        emoji: {
            first: "🔅",
            second: "🔆",
            time: 750
        },
        sign: "VueShell $",
        img: {
            align: "left",
            width: 100,
            height: 100
        }
      },
      commands: [
        { 
          name: "info",
          get() {
            return `<p>With ❤️ By Salah Bentayeb @halasproject.</p>`;
        }
        },
        {
          name: "uname",
          get() {
            return navigator.appVersion;
          }
        },
        {
          name: "node -v",
          get() {
            return navigator.appVersion;
          }
        }
        
      ]
    };
  },
  methods: {
    prompt(value) {
      if (value == "node -v") {
        this.send_to_terminal = process.versions.node;
      }
    }
  }
}
</script>
 
<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  font-size: 70px;
}
</style>