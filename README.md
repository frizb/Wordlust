# Wordlust
Wordlust is a Password Base Wordlist for Hashcat Mutator Rules. Most passwords today are a combination of one or more words with some mutators.  For example, we often see the password baseword of "password" with mutations such as:
* 123Password!
* P@55w0rd1
* SummerPassword1993
* password12#$

Hashcat is MUCH faster at generating mutations on the fly than running through wordlists. Here is my benchmark from an Nvidia GeForce RTX 2060:
* Hashcat Wordlist Speed: 12000 kH/s
* Hashcat Wordlist Mutation Speed: 6682.3 MH/s

Wordlust is based on the assumption that it is more efficient to create a large list of password "base" words rather than mutating existing known passwords.
Wordlust is a wordlist comprised of known bad password "base" words and other wordlists. Other people have done most of the work to curate this list, I mostly just rammed them all together into one file to use as a mutation base.

# How was Wordlust created?

To create this list, I processed multiple leaked / cracked passwords lists and:
1. removed all the mutation characters (numbers and symbols) and lowercased them all. 
2. Un-leet speaked the words to get the base word list (@->A, $->S) etc.

Also I combined it with many dictionaries of words such as english dictionary words, cities, names, company names, sports teams, computer terms, default passwords, keyboard character runs, celebrity names, universities, movies, movie quotes, phrases, song lyrics, book titles and many more.

Finally, I lowercase everything and remove any duplicates and sort them alphabetically. 

# How to use Wordlust?

I recommend using them with hashcat and a set of mutator rules such as:
https://www.notsosecure.com/one-rule-to-rule-them-all/

For example, to crack a hashlist of NTLM passwords, I would use the following command:
```
hashcat64 -m 1000 -a 0 -w 4 --force -O c:\HASHES\hashsample.hash c:\WORDLISTS\wordlust.txt -r OneRuleToRuleThemAll.rule
```

## References:
This word list contains many, many sources.  As new sources are added, I include them on this list of references:
* http://www.adeptus-mechanicus.com/codex/hashpass/hashpass.php
* https://labs.nettitude.com/blog/rocktastic/
* https://www.reddit.com/r/DataHoarder/comments/6rbigw/306_million_freely_downloadable_pwned_passwords/
* https://wordlists.capsop.com/
* https://github.com/danielmiessler/SecLists
* https://weakpass.com/links
* https://github.com/initstring/lyricpass/
* https://github.com/initstring/passphrase-wordlist
* https://hashes.org/hashlists.php
