<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          ようこそ！
        </v-card-title>
        <v-card-text>
          <p>EVM赤ちゃんをEVM幼稚園生にする、<br>ちょっとEあぷりです。</p>
        </v-card-text>
        <v-card-actions>
          <v-form>
            <v-container>
              <v-row>
                <v-col cols="4">
                  <v-subheader>BAC</v-subheader>
                </v-col>
                <v-col cols="8">
                  <v-text-field
                    v-model="form.f_bac"
                    value="10.00"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="4">
                  <v-subheader>PV</v-subheader>
                </v-col>
                <v-col cols="8">
                  <v-text-field
                    v-model="form.f_pv"
                    value="10.00"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="4">
                  <v-subheader>AC</v-subheader>
                </v-col>
                <v-col cols="8">
                  <v-text-field
                    v-model="form.f_ac"
                    value="10.00"
                  ></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="4">
                  <v-subheader>EV</v-subheader>
                </v-col>
                <v-col cols="8">
                  <v-text-field
                    v-model="form.f_ev"
                    value="10.00"
                  ></v-text-field>
                </v-col>
              </v-row>
            </v-container>
          </v-form>
        </v-card-actions>
        <v-card-actions>
          <v-container>
            <v-row>
              <v-btn
                color="primary"
                nuxt
              >
                Continue
              </v-btn>
              <!--
              <v-dialog
                v-model="dialog"
                fullscreen
                hide-overlay
                transition="dialog-bottom-transition"
              >
                <v-spacer />
                <template v-slot:activator="{ on, attrs }">
                  <v-btn
                    color="primary"
                    nuxt
                    v-bind="attrs"
                    v-on="on"
                    @click="calc"
                  >
                    Continue
                  </v-btn>
                </template>
                <v-card>
                  <v-card-title class="text-h5 grey lighten-2">
                    判定結果！
                  </v-card-title>

                  <v-card-text>
                    めっちゃ順調です！
                  </v-card-text>

                  <v-divider></v-divider>

                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                      color="primary"
                      text
                      @click="dialog = false;"
                    >
                      戻る
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
              -->
            </v-row>
          </v-container>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage',
  data () {
    return {
      form: {
        f_bac: "",
        f_pv: "",
        f_ac: "",
        f_ev: "",
        r_sv: "",
      },
      valid: true,
      dialog: false,
      rules: {
        required: value => !!value || '入力してください',
        email: value => /.+@.+\\..+/.test(value) || 'メールアドレスの形式が正しくありません',
        tel: value => /^(0[5-9]0[0-9]{8}|0[1-9][1-9][0-9]{7})$/.test(value.replace(/[━.*‐.*―.*－.*\-.*ー.*\-]/gi, ''))|| '電話番号の形式が正しくありません',
        max: value => (value && value.length <= 100) || '100文字以下で入力してください',
      },
    }
  },
  methods: {
    submit () {
      // バリデーションチェック
      if(this.$refs.form.validate()) {
        // 送信処理
        // (...省略)
        // 入力値を初期化する
        this.$refs.form.reset()
      }
    },
    calc() {
      r_sv=this.$refs.form.f_ev - this.$refs.form.f_pv;
      console.log(r_sv);
      console.log('test');
    }
  },
}
</script>
