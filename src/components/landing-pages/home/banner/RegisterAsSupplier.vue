<template>
        <div>
            <div :style="step === 0 ? 'display:block': 'display:none' " class="con-tab-ejemplo custForm-height">

                <div class="form-group">
                    <label>{{$t('SupCompanmyName')}}</label>
                    <input type="email" class="form-control">
                </div>

                <div class="form-group">
                    <label>{{$t('Authorizer')}}</label>
                    <input type="password" class="form-control">
                </div>

                <div class="form-group">
                    <label>{{$t('AuthorizerPosition')}}</label>
                    <input type="email" class="form-control">
                </div>
            </div>
            <div :style="step === 1 ? 'display:block': 'display:none' " class="con-tab-ejemplo custForm-height">

                <div class="form-group">
                    <input type="email" class="form-control" :placeholder="$t('LoginEmail')" >
                </div>

                <div class="form-group">
                    <input type="email" class="form-control" :placeholder="$t('LoginEmail')" >
                </div>

                <div class="form-group">
                    <b-form-input size="sm" :placeholder="$t('ContactNumber')" />
                </div>
                <div class="form-group">
                    <b-form-input size="sm" :placeholder="$t('Address')" />
                </div>
            </div>
            <div :style="step === 2 ? 'display:block': 'display:none' " class="con-tab-ejemplo custForm-height">
                <div class="form-group">
                    <b-form-input size="sm" :placeholder="$t('CompanyRegistryNumber')" />
                </div>

                <b-form-group label="上傳商業登記證證明" label-for="file" label-cols="5" label-size="sm">
                        <b-form-file class="mt-2"  id="file" size="sm" v-model="file" />
                </b-form-group>
            </div>
            <div :style="step === 3 ? 'display:block': 'display:none' " class="con-tab-ejemplo custForm-height">

                <p>{{$t('PaymentInfo')}}</p>
                <b-form-group>
                    <b-form-input size="sm" :placeholder="$t('BankName')" />
                </b-form-group>

                <b-form-group>
                    <b-form-input size="sm" :placeholder="$t('BankAccountNo')" />
                </b-form-group>

                <b-form-group>
                    <b-form-input size="sm" :placeholder="$t('PaypalNo')" />
                </b-form-group>
            </div>
            <b-button class="btn btn-primary" @click="submit($t('ThanksSubmitRegTitle'), $t('ThanksSubmitRegContent'))">{{step === 3? $t('Submit') : $t('Next')}}</b-button>
            <p style="color:#c679e3; margin-bottom:88.25px;">{{$t('RfqWritingFee')}}</p>

        </div>
</template>

<script>
    export default {
        name: "RegisterAsSupplier",
        data(){
            return {
                step: 0,
                file: null,
            }
        },
        methods:{
            submit(title, content){
                if (this.step === 3){
                    this.$swal(title, content, "success")
                    this.step = 0
                    return
                }
                this.step ++
            }
        }
    }
</script>

<style lang="scss" scoped>
    .custForm-height{
        min-height: 337px;
    }

    .form-group {
    label {
        font-size: 22px;
        color: #c679e3;
        font-weight: 600;
    }
    }
</style>
