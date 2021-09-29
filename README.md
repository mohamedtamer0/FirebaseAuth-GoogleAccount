# FirebaseAuth-GoogleAccount



```gradle
dependencies {
   implementation 'com.google.firebase:firebase-auth-ktx:21.0.1'
   implementation 'com.firebaseui:firebase-ui-auth:7.2.0'
   }
```


```kotlin
    companion object {
        private const val RC_SIGN_IN = 9001
    }
    
  private lateinit var auth: FirebaseAuth

  private lateinit var googleSignInClient: GoogleSignInClient

    ========================================
            auth = Firebase.auth
        
        // Configure Google Sign In
        val gso = GoogleSignInOptions.Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
            .requestIdToken(getString(R.string.default_web_client_id))
            .requestEmail()
            .build()

        googleSignInClient = GoogleSignIn.getClient(this, gso)

        btn_google_sign_in.setOnClickListener {
            signIn()
        }
        
        =============================
        
        private fun firebaseAuthWithGoogle(idToken: String) {
        val credential = GoogleAuthProvider.getCredential(idToken, null)
        auth.signInWithCredential(credential)
            .addOnCompleteListener(this) { task ->
                if (task.isSuccessful) {
                    // Sign in success, update UI with the signed-in user's information
                    Toast.makeText(this, "signInWithCredential:success", Toast.LENGTH_LONG).show()
                    val user = auth.currentUser
                    updateUI(user)
                } else {
                    // If sign in fails, display a message to the user.
                    Toast.makeText(this, "signInWithCredential:failure", Toast.LENGTH_LONG).show()
                    updateUI(null)
                }
            }
    }
        
    
    


```


![Screenshot_1632959237](https://user-images.githubusercontent.com/51374446/135363591-f6b50449-db15-46dc-811c-a0df04e54051.png)
