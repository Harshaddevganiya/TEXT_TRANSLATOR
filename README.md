bulid.gradle ---> +Add


android { ->
-----------------------------------------

 buildFeatures{
        dataBinding true
    }
-----------------------------------------
}

dependencies { -->

    androidTestImplementation 'androidx.test.espresso:espresso-core:3.5.0'
  implementation 'com.google.mlkit:translate:17.0.1'

}
