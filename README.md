# Words

A list of english words with their relative frequencies.

## How it was assembled

1. I took the "1/3 million most frequent words, all lowercase, with counts" from https://norvig.com/ngrams/
2. It contains many questionable words, so I intersected it with `words_alpha.txt` from https://github.com/dwyl/english-words

```shell
curl https://norvig.com/ngrams/count_1w.txt | sd '\t' ',' > count_1w.txt
curl https://raw.githubusercontent.com/dwyl/english-words/master/words_alpha.txt > words_alpha.txt
qsv join -n 1 count_1w.txt 1 words_alpha.txt | qsv select 1,2 > words.txt
```
