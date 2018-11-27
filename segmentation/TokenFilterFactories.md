## solr.EdgeNGramFilterFactory
这个FilterFactory主要用于前缀匹配或后缀匹配(side="back") 主要设置有minGramSize 和maxGramSize。比如正向EdgeNGram，minGramSize为1，maxGramSize为5，给定一个字符串car,经过EdgeNGramFilterFactory后，会分割为c,ca,car；给定一个字符串number，经过EdgeNGramFilterFactory后，会分割为n,nu,num,numb,numbe

## solr.LowerCaseFilterFactory
把大写字母转换成对应的小写字母