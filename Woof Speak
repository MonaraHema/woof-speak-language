import tkinter as tk
from tkinter import messagebox

# Consonants (lowercase)
consonants = {
    'b': "ruff",
    'c': "rruff",
    'd': "rrruff",
    'f': "rrrruff",
    'g': "rrrrruff",
    'h': "rrrrrruff",
    'j': "rrrrrrruff",
    'k': "wuff",
    'l': "wwuff",
    'm': "wwwuff",
    'n': "wwwwuff",
    'p': "wwwwwuff",
    'q': "wwwwwwuff",
    'r': "wwwwwwwuff",
    's': "bark",
    't': "bbark",
    'v': "bbbark",
    'w': "bbbbark",
    'x': "bbbbbark",
    'y': "bbbbbbark",
    'z': "bbbbbbbark"
}

# Vowels (lowercase)
vowels = {
    'a': "awoo",
    'e': "awooo",
    'i': "awoooo",
    'o': "awooooo",
    'u': "awoooooo"
}

# Uppercase vowels use "woof" base
vowels_upper = {
    'A': "woof",
    'E': "wooof",
    'I': "woooof",
    'O': "wooooof",
    'U': "woooooof"
}

# Punctuation and special characters
specials = {
    ' ': "huff",
    '\n': "yip",
    ',': "yap",
    '.': "arf",
    '!': "grr!",
    '?': "grrr?",
    ':': "ruff-ruff",
    ';': "ruff-wuff"
}

# Numbers (0-9)
numbers = {
    '0': "grr",
    '1': "grrr",
    '2': "grrrr",
    '3': "grrrrr",
    '4': "grrrrrr",
    '5': "grrrrrrr",
    '6': "grrrrrrrr",
    '7': "grrrrrrrrr",
    '8': "grrrrrrrrrr",
    '9': "grrrrrrrrrrr"
}

# Build the complete english-to-woof dictionary for lowercase letters & numbers & punctuation
eng_to_woof = {}
for letter, code in consonants.items():
    eng_to_woof[letter] = code
for letter, code in vowels.items():
    eng_to_woof[letter] = code
for digit, code in numbers.items():
    eng_to_woof[digit] = code
for char, code in specials.items():
    eng_to_woof[char] = code

# For uppercase letters, we use a prefix "yip " + lowercase token.
def encode_letter(ch):
    if ch.isupper():
        if ch in vowels_upper:
            return "yip " + vowels_upper[ch]
        else:
            lower = ch.lower()
            if lower in eng_to_woof:
                return "yip " + eng_to_woof[lower]
            else:
                return ch
    else:
        return eng_to_woof.get(ch, ch)

def english_to_woof_translate(text):
    result_tokens = []
    for ch in text:
        result_tokens.append(encode_letter(ch))
    return " ".join(result_tokens)

woof_to_eng = {}
for k, v in eng_to_woof.items():
    woof_to_eng[v] = k

for k, v in vowels_upper.items():
    woof_to_eng[v] = k

def decode_token(token):
    if token.startswith("yip "):
        inner = token[4:]
        letter = woof_to_eng.get(inner, None)
        if letter:
            return letter.upper()
        else:
            return inner.upper()
    else:
        return woof_to_eng.get(token, token)

def woof_to_english_translate(text):
    tokens = text.split()
    decoded_chars = []
    for token in tokens:
        decoded_chars.append(decode_token(token))
    return "".join(decoded_chars)

def translate_eng_to_woof():
    input_text = english_text.get("1.0", tk.END).rstrip("\n")
    if not input_text:
        messagebox.showerror("Error", "Please enter English text to translate.")
        return
    output = english_to_woof_translate(input_text)
    woof_text.delete("1.0", tk.END)
    woof_text.insert(tk.END, output)

def translate_woof_to_eng():
    input_text = woof_text.get("1.0", tk.END).rstrip("\n")
    if not input_text:
        messagebox.showerror("Error", "Please enter Woof Speak text to translate.")
        return
    output = woof_to_english_translate(input_text)
    english_text.delete("1.0", tk.END)
    english_text.insert(tk.END, output)

root = tk.Tk()
root.title("Woof Speak Translator")

eng_frame = tk.LabelFrame(root, text="English")
eng_frame.pack(fill="both", expand=True, padx=10, pady=5)
english_text = tk.Text(eng_frame, height=10, wrap=tk.WORD)
english_text.pack(fill="both", expand=True, padx=5, pady=5)

woof_frame = tk.LabelFrame(root, text="Woof Speak")
woof_frame.pack(fill="both", expand=True, padx=10, pady=5)
woof_text = tk.Text(woof_frame, height=10, wrap=tk.WORD)
woof_text.pack(fill="both", expand=True, padx=5, pady=5)

btn_frame = tk.Frame(root)
btn_frame.pack(pady=10)

btn_eng_to_woof = tk.Button(btn_frame, text="English → Woof Speak", command=translate_eng_to_woof)
btn_eng_to_woof.pack(side=tk.LEFT, padx=5)

btn_woof_to_eng = tk.Button(btn_frame, text="Woof Speak → English", command=translate_woof_to_eng)
btn_woof_to_eng.pack(side=tk.LEFT, padx=5)

root.mainloop()
