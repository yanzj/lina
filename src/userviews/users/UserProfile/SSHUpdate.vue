<template>
  <IBox>
    <GenericCreateUpdateForm
      :fields="fields"
      :fields-meta="fieldsMeta"
      :initial="object"
      :url="url"
      :get-method="getMethod"
      :more-buttons="moreButtons"
    />
  </IBox>
</template>

<script>
import GenericCreateUpdateForm from '@/layout/components/GenericCreateUpdateForm'
import { IBox } from '@/components'

export default {
  name: 'SSHUpdate',
  components: {
    GenericCreateUpdateForm,
    IBox
  },
  props: {
    object: {
      type: Object,
      default: null
    }
  },
  data() {
    return {
      url: '/api/v1/users/profile/public-key/',
      fields: [
        [this.$t('users.OldSSHKey'), ['public_key_comment', 'public_key_hash_md5']],
        [this.$t('users.UpdateSSHKey'), ['public_key']]
      ],
      fieldsMeta: {
        public_key_comment: {
          label: this.$t('users.Name'),
          disabled: true
        },
        public_key_hash_md5: {
          label: this.$t('users.FingerPrint'),
          disabled: true
        },
        public_key: {
          el: {
            type: 'textarea',
            placeholder: 'ssh-rsa AAAA...'
          },
          helpText: this.$t('users.HelpText.SSHKeyOfProfileSSHUpdatePage')
        }
      },
      moreButtons: [
        {
          title: this.$t('users.ResetAndDownloadSSHKey'),
          callback: function() {
            window.open(`/core/auth/profile/pubkey/generate/`, '_blank')
          }
        }
      ]
    }
  },
  methods: {
    getMethod() {
      return 'put'
    }
  }
}
</script>

<style scoped>

</style>
