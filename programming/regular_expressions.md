# Regular expressions

## Character codes

| Regex    | Explanation                                               | Example                                                   |
| ---      | ---                                                       | ---                                                       |
| \[abc\]  | Matches any of the included characters                    | **\[Y9!\]** matches: I am `9` years old `Y`ay`!`          |
| \[^abc\] | Matches any characters NOT specified in brackets          | matches: `p`u`mpk`i`ns` a`r`e o`r`a`ng`e                  |
| \[a-z\]  | Matches any characters within specific range              | **\[1-3a-c\]** matches: 76`a321bca`9z                     |
| .        | Matches any character except linebreaks                   | **.**  matches: `hello world 3342`                        |
| \w       | Matches any word character, equivalent to \[A-Za-z0-9\_\] | **\w** matches: `Regexps are amazing`!!!                  |
| \d       | Matches numeric digits                                    | **\d** matches: My number is +\(`82`\)-`10`-`8238`-`0032` |
| \s       | Matches any whitespace \(spaces, tabs,linebreaks\)        | **\s** matches: I```love`` `apple` \`pie                  |

## Quantifiers & More

| Regex | Explanation | Example |
| --- | --- | --- |
| + | Matches 1 or more of preceding token | **A+** matches: H`A` H`A` H`AAA` |
| \* | Matches zero or more of the previous token | **colou\*r** matches: is it `color` or `colour` or `colouuuur` |
| {3} | Matches specific quantity of previous token | **\[a-z\]{3}** matches: `she` is a `cat` `not` a `dog` |
| {1,3} | Matches quantity within specified range | **\d{3,4}** matches: `010`-`8238`-`0032` |
| {4,} | Matches the specified quantity or greater | **!{3,}** matches: hi! this is great`!!!`lol`!!!!!` |
| ? | Matches 0 or 1 of previous token. Basically it makes something optional | **colou?r** matches: is it `color` or `colour` or colouuuur? |
| \| | Matches whatever is to the left or right of the **\|** character. Similar to boolean OR. | \*\*\w+pp\(y\|ies\) matches: `puppy` `puppies` `poppy` `poppies` `yuppy` `yuppies` |

## Anchors

| Regex | Explanation | Example |
| :--- | :--- | :--- |
| ^ | Matches the beginning of a string | **\^\[Pp\]** matches: `P`ickle people |
| $ | Matches the end of a string | **ah$** matches: hahahah`ah` |

