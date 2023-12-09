TranslateLanguage - All languages Add in project

package com.sunayanpradhan.texttranslator

import android.os.Bundle
import android.widget.ArrayAdapter
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.databinding.DataBindingUtil
import com.google.mlkit.common.model.DownloadConditions
import com.google.mlkit.nl.translate.TranslateLanguage
import com.google.mlkit.nl.translate.Translation
import com.google.mlkit.nl.translate.TranslatorOptions
import com.sunayanpradhan.texttranslator.databinding.ActivityMainBinding

class MainActivity : AppCompatActivity() {
    lateinit var binding: ActivityMainBinding
    private var items =
        arrayOf("Afrikaans",
            "Arabic",
            "Bengali",
            "Belarusian",
            "Bulgarian",
            "Catalan",
            "Chinese",
            "Croatian",
            "Czech",
            "English",
            "Esperanto",
            "Estonian",
            "French",
            "Finnish",
            "Galician",
            "Georgian",
            "Gujarati",
            "German",
            "Greek",
            "Hebrew",
            "Hindi",
            "Hungarian",
            "Indonesian",
            "Icelandic",
            "Italian",
            "Japanese",
            "Kannada",
            "Korean",
            "Latvian",
            "Lithuanian",
            "Macedonian",
            "Maltese",
            "Malay",
            "Marathi",
            "Norwegian",
            "Persian",
            "Polish",
            "Portuguese",
            "Romanian",
            "Russian",
            "Slovak",
            "Slovenian",
            "Spanish",
            "Swahili",
            "Swedish",
            "Tamil",
            "Telugu",
            "Thai",
            "Turkish",
            "Urdu",
            "Ukrainian",
            "Vietnamese"
        )
    private var conditions = DownloadConditions.Builder()
        .requireWifi()
        .build()

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        binding = DataBindingUtil.setContentView(this, R.layout.activity_main)

        val itemsAdapter: ArrayAdapter<String> = ArrayAdapter(
            this,
            android.R.layout.simple_dropdown_item_1line, items
        )

        binding.languageFrom.setAdapter(itemsAdapter)

        binding.languageTo.setAdapter(itemsAdapter)

        binding.translate.setOnClickListener {

            val options = TranslatorOptions.Builder()
                .setSourceLanguage(selectFrom())
                .setTargetLanguage(selectTo())
                .build()

            val englishGermanTranslator = Translation.getClient(options)

            englishGermanTranslator.downloadModelIfNeeded(conditions)
                .addOnSuccessListener {

                    englishGermanTranslator.translate(binding.input.text.toString())
                        .addOnSuccessListener { translatedText ->

                            binding.output.text = translatedText

                        }
                        .addOnFailureListener { exception ->

                            Toast.makeText(this, exception.message, Toast.LENGTH_SHORT).show()

                        }


                }
                .addOnFailureListener { exception ->

                    Toast.makeText(this, exception.message, Toast.LENGTH_SHORT).show()

                }


        }


    }

    private fun selectFrom(): String {

        return when (binding.languageFrom.text.toString()) {

            "" -> TranslateLanguage.ENGLISH

            "Afrikaans" -> TranslateLanguage.AFRIKAANS

            "Arabic" -> TranslateLanguage.ARABIC

            "Bengali" -> TranslateLanguage.BENGALI

            "Belarusian" -> TranslateLanguage.BELARUSIAN

            "Bulgarian" -> TranslateLanguage.BULGARIAN

            "Catalan" -> TranslateLanguage.CATALAN

            "Chinese" -> TranslateLanguage.CHINESE

            "Croatian" -> TranslateLanguage.CROATIAN

            "Czech" -> TranslateLanguage.CZECH

            "English" -> TranslateLanguage.ENGLISH

            "Esperanto" -> TranslateLanguage.ESPERANTO

            "Estonian" -> TranslateLanguage.ESTONIAN

            "French" -> TranslateLanguage.FRENCH

            "Finnish" -> TranslateLanguage.FINNISH

            "Galician" -> TranslateLanguage.GALICIAN

            "Georgian" -> TranslateLanguage.GEORGIAN

            "Gujarati" -> TranslateLanguage.GUJARATI

            "German" -> TranslateLanguage.GERMAN

            "Greek" -> TranslateLanguage.GREEK

            "Hebrew" -> TranslateLanguage.HEBREW

            "Hindi" -> TranslateLanguage.HINDI

            "Hungarian" -> TranslateLanguage.HUNGARIAN

            "Indonesian" -> TranslateLanguage.INDONESIAN

            "Icelandic" -> TranslateLanguage.ICELANDIC

            "Italian" -> TranslateLanguage.ITALIAN

            "Japanese" -> TranslateLanguage.JAPANESE

            "Kannada" -> TranslateLanguage.KANNADA

            "Korean" -> TranslateLanguage.KOREAN

            "Latvian" -> TranslateLanguage.LATVIAN

            "Lithuanian" -> TranslateLanguage.LITHUANIAN

            "Macedonian" -> TranslateLanguage.MACEDONIAN

            "Maltese" -> TranslateLanguage.MALTESE

            "Malay" -> TranslateLanguage.MALAY

            "Marathi" -> TranslateLanguage.MARATHI

            "Norwegian" -> TranslateLanguage.NORWEGIAN

            "Persian" -> TranslateLanguage.PERSIAN

            "Polish" -> TranslateLanguage.POLISH

            "Portuguese" -> TranslateLanguage.PORTUGUESE

            "Romanian" -> TranslateLanguage.ROMANIAN

            "Russian" -> TranslateLanguage.RUSSIAN

            "Slovak" -> TranslateLanguage.SLOVAK

            "Slovenian" -> TranslateLanguage.SLOVENIAN

            "Spanish" -> TranslateLanguage.SPANISH

            "Swahili" -> TranslateLanguage.SWAHILI

            "Swedish" -> TranslateLanguage.SWEDISH

            "Tamil" -> TranslateLanguage.TAMIL

            "Telugu" -> TranslateLanguage.TELUGU

            "Thai" -> TranslateLanguage.THAI

            "Turkish" -> TranslateLanguage.TURKISH

            "Urdu" -> TranslateLanguage.URDU

            "Ukrainian" -> TranslateLanguage.UKRAINIAN

            "Vietnamese" -> TranslateLanguage.VIETNAMESE

            else -> TranslateLanguage.ENGLISH

        }


    }

    private fun selectTo(): String {

        return when (binding.languageTo.text.toString()) {

            "" -> TranslateLanguage.HINDI

            "Afrikaans" -> TranslateLanguage.AFRIKAANS

            "Arabic" -> TranslateLanguage.ARABIC

            "Bengali" -> TranslateLanguage.BENGALI

            "Belarusian" -> TranslateLanguage.BELARUSIAN

            "Bulgarian" -> TranslateLanguage.BULGARIAN

            "Catalan" -> TranslateLanguage.CATALAN

            "Chinese" -> TranslateLanguage.CHINESE

            "Croatian" -> TranslateLanguage.CROATIAN

            "Czech" -> TranslateLanguage.CZECH

            "English" -> TranslateLanguage.ENGLISH

            "Esperanto" -> TranslateLanguage.ESPERANTO

            "Estonian" -> TranslateLanguage.ESTONIAN

            "French" -> TranslateLanguage.FRENCH

            "Finnish" -> TranslateLanguage.FINNISH

            "Galician" -> TranslateLanguage.GALICIAN

            "Georgian" -> TranslateLanguage.GEORGIAN

            "Gujarati" -> TranslateLanguage.GUJARATI

            "German" -> TranslateLanguage.GERMAN

            "Greek" -> TranslateLanguage.GREEK

            "Hebrew" -> TranslateLanguage.HEBREW

            "Hindi" -> TranslateLanguage.HINDI

            "Hungarian" -> TranslateLanguage.HUNGARIAN

            "Indonesian" -> TranslateLanguage.INDONESIAN

            "Icelandic" -> TranslateLanguage.ICELANDIC

            "Italian" -> TranslateLanguage.ITALIAN

            "Japanese" -> TranslateLanguage.JAPANESE

            "Kannada" -> TranslateLanguage.KANNADA

            "Korean" -> TranslateLanguage.KOREAN

            "Latvian" -> TranslateLanguage.LATVIAN

            "Lithuanian" -> TranslateLanguage.LITHUANIAN

            "Macedonian" -> TranslateLanguage.MACEDONIAN

            "Maltese" -> TranslateLanguage.MALTESE

            "Malay" -> TranslateLanguage.MALAY

            "Marathi" -> TranslateLanguage.MARATHI

            "Norwegian" -> TranslateLanguage.NORWEGIAN

            "Persian" -> TranslateLanguage.PERSIAN

            "Polish" -> TranslateLanguage.POLISH

            "Portuguese" -> TranslateLanguage.PORTUGUESE

            "Romanian" -> TranslateLanguage.ROMANIAN

            "Russian" -> TranslateLanguage.RUSSIAN

            "Slovak" -> TranslateLanguage.SLOVAK

            "Slovenian" -> TranslateLanguage.SLOVENIAN

            "Spanish" -> TranslateLanguage.SPANISH

            "Swahili" -> TranslateLanguage.SWAHILI

            "Swedish" -> TranslateLanguage.SWEDISH

            "Tamil" -> TranslateLanguage.TAMIL

            "Telugu" -> TranslateLanguage.TELUGU

            "Thai" -> TranslateLanguage.THAI

            "Turkish" -> TranslateLanguage.TURKISH

            "Urdu" -> TranslateLanguage.URDU

            "Ukrainian" -> TranslateLanguage.UKRAINIAN

            "Vietnamese" -> TranslateLanguage.VIETNAMESE


            else -> TranslateLanguage.HINDI

        }


    }

}




        
