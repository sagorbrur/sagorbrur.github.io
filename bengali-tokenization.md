# Bengali Tokenization Using CLTK


```python
from cltk.tokenize.sentence import TokenizeSentence

sentence = "আমার সোনার বাংলা আমি তোমায় ভালোবাসি।"

tokenizer = TokenizeSentence('bengali')

bengali_text_tokenize = tokenizer.tokenize(sentence)

print(bengali_text_tokenize)
#output: ['আমার', 'সোনার', 'বাংলা', 'আমি', 'তোমায়', 'ভালোবাসি', '।']

```


## References
[http://docs.cltk.org/en/latest/bengali.html](http://docs.cltk.org/en/latest/bengali.html)
