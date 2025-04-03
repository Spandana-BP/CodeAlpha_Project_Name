from googletrans import Translator

def translate_text(text, src_lang, dest_lang):
    translator = Translator()
    try:
        translated = translator.translate(text, src=src_lang, dest=dest_lang)
        return translated.text
    except Exception as e:
        return f"Translation Error: {e}"

if __name__ == "__main__":
    text = input("Enter text to translate: ")
    print("Choose source language (en for English, kn for Kannada, auto for detect): ")
    src_lang = input().strip()
    print("Choose target language (en for English, kn for Kannada): ")
    dest_lang = input().strip()
    
    translated_text = translate_text(text, src_lang, dest_lang)
    print(f"Translated Text: {translated_text}") 