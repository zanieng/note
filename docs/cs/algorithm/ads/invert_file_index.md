# Invert File Index（倒排索引）
## Term-Document Incidence Matrix 文档关联矩阵
- a matrix of the appearance of each word in each doc
  + 行是词，列是文档号；(i,j)表明第i个词是否在第j篇文章出现
- 如果单词在某篇文章中出现，则对应的矩阵上位置的值为1，否则为0，若干篇文章的出现情况可以得到若干个二进制字符串
  + 只关注一个单词出现与否，并不关注出现的频率，也找不出单词在文章的哪个位置
  + 一个短语调换顺序也会被找出来，不过我们不关注顺序，重要的是出现与否
- 用逻辑运算可以考察单词在doc中的出现情况
  + 位运算取交一下，快速排序，从频率低的开始交，这样效率高
  
## Inverted File Index 倒排文件索引
- Index is a mechanism for locating a given term in a text 一种在文章中定位给定单词的机制
- Inverted File contains a list of pointers to all occurrences of that term in the text
  + 索引的方式 单词---<次数；依次列出每一篇出现的doc的编号>
  + 更好的索引方式 单词----<次数；(出现的doc的编号；该doc中每一个出现的位置)>
- Index generator 索引生成器
  1. 从文件中读取词
  2. 将该词提取为词干(word stemming)，即去除第三人称形式、过去式、进行时等形式，留下词干），并去除分词(stop word)，即”a”, “is”等没有意义的词。
  3. 检查该词是否已经在词典之中。
  4. 若不在，则将该词添加入词典之中。更新索引信息。
  5. 建立完毕后，将索引文件存入磁盘

