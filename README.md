- 👋 Hi, I’m @Zain35145
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Zain35145/Zain35145 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import random
import string

def word_frequency_analysis(sentence):
    words = sentence.split()
    word_freq = {}
    for word in words:
        word_freq[word] = word_freq.get(word, 0) + 1
    return word_freq

def sentence_maker(words, num_sentences):
    sentences = []
    for _ in range(num_sentences):
        sentence = ' '.join(random.choices(words, k=5))
        sentences.append(sentence)
    return sentences

def longest_shortest_word_finder(sentence):
    words = sentence.split()
    words_length = [len(word) for word in words]
    max_length = max(words_length)
    min_length = min(words_length)
    longest_words = [word for word in words if len(word) == max_length]
    shortest_words = [word for word in words if len(word) == min_length]
    return longest_words, shortest_words

def word_search(sentence, word):
    word_count = sentence.lower().count(word.lower())
    if word_count > 0:
        return f'The word "{word}" appears {word_count} time(s) in the sentence.'
    else:
        return f'The word "{word}" does not exist in the sentence.'

def palindrome_detector(sentence):
    words = sentence.split()
    palindromic_words = [word for word in words if word.lower() == word.lower()[::-1]]
    if palindromic_words:
        return palindromic_words
    else:
        return 'There are no palindromic words in the sentence.'

def vowel_consonant_counter(sentence):
    vowels = 'aeiou'
    words = sentence.split()
    count_result = {}
    for word in words:
        vowel_count = sum(char in vowels for char in word.lower())
        consonant_count = len(word) - vowel_count
        count_result[word] = (vowel_count, consonant_count)
    return count_result

def remove_punctuation(sentence):
    return sentence.translate(str.maketrans('', '', string.punctuation))

def analyze_text():
    sentence = input("Enter a sentence: ")
    sentence = remove_punctuation(sentence)

    # 1) Word Frequency Analysis
    word_freq = word_frequency_analysis(sentence)
    print("\nWord Frequency Analysis:")
    for word, freq in word_freq.items():
        print(f'"{word}": {freq}')

    # 2) Sentence Maker
    num_sentences = int(input("Enter a number N: "))
    sentences = sentence_maker(sentence.split(), num_sentences)
    print("\nGenerated Sentences:")
    for i, sentence in enumerate(sentences):
        print(f'{i+1}. {sentence}')

    # 3) Longest and Shortest Word Finder
    longest_words, shortest_words = longest_shortest_word_finder(sentence)
    print("\nLongest word(s):")
    for word in longest_words:
        print(f'"{word}"')
    print("\nShortest word(s):")
    for word in shortest_words:
        print(f'"{word}"')

    # 4) Word Search
    search_word = input("Enter a word to search: ")
    search_result = word_search(sentence, search_word)
    print("\nWord Search:")
    print(search_result)

    # 5) Palindrome Detector
    palindromic_words = palindrome_detector(sentence)
    print("\nPalindrome Detector:")
    if isinstance(palindromic_words, list):
        for word in palindromic_words:
            print(f'"{word}"')
    else:
        print(palindromic_words)

    # 6) Vowel/Consonant Counter
    count_result = vowel_consonant_counter(sentence)
    print("\nVowel/Consonant Counter:")
    for word, counts in count_result.items():
        vowel_count, consonant_count = counts
        print(f'"{word}": {vowel_count} vowel(s) and {consonant_count} consonant(s)')

analyze_text()
