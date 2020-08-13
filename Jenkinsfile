node {
    
	 stage('Check out')
	  {
	 echo "Clone git Code repo"
      }
	 
	 stage('Vault')
	 
	 withCredentials([[$class: 'VaultTokenCredentialBinding', addrVariable: 'VAULT_ADDR', 
	 credentialsId: 'VaultToken', tokenVariable: 'VAULT_TOKEN', vaultAddr: 'http://54.226.41.254:8200']]) {
     
	 sh '''
      
	  curl --header "X-Vault-Token: $VAULT_TOKEN" --request GET http://54.226.41.254:8200/v1/myengine/ssl1/cert |jq -r '.data."cert"' > .cert.pem
	  

      curl --header "X-Vault-Token: $VAULT_TOKEN" --request GET http://54.226.41.254:8200/v1/myengine/ssl2/key |jq -r '.data."key"' > .selfsigned.pem

      
	  ls -la
	  date
	  cat .cert.pem
	  cat .selfsigned.pem
	  
	  
	'''
	 
	 }

}
