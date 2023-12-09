bulid.gradle ---> +Add


android { ->
-----------------------------------------

 buildFeatures{
        dataBinding true
    }
-----------------------------------------
}

dependencies { -->

  implementation 'com.google.mlkit:translate:17.0.1'

}
