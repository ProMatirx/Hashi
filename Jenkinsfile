node {
    
	 stage('Check out')
	  {
	 echo "Clone git Code repo"
      }
	 
	 stage('Vault')
	 
	 withCredentials([[$class: 'VaultTokenCredentialBinding', addrVariable: 'VAULT_ADDR', 
	 credentialsId: 'VaultToken', tokenVariable: 'VAULT_TOKEN', vaultAddr: 'http://34.238.150.94:8200']]) {
     
	 sh '''
   
      vault kv get -field=key kv-sec/openssl/secrets/pem >.cert.pem
      vault kv get -field=self kv-sec/openssl/selfsigned/cert >.selfsigned.key

      ##curl --header "X-Vault-Token: $VAULT_ADDR" --request GET http://54.147.197.25:8200/v1/myengine/ssl1/cert

      ##curl --header "X-Vault-Token: $VAULT_ADDR" --request GET http://54.147.197.25:8200/v1/myengine/ssl2/key

	  ls -la
	'''
	 
	 
	 }

}
