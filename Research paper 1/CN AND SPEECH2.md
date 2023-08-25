
# Speech to SQL Generator - A Voice Based Approach

**Abstract:**

* Recent developments in speech recognition system and natural language processing have given rise to
a new generation of powerful voice-based interfaces. In this proposed system, a user interacts with the system through a voice-based user interface to fetch the desired results.
* To make the system smooth and interactive, the query is based on casual human speech / conversation. The spoken
query undergoes many steps to arrive at the final results. 
* It includes synonym table which is used to convert the spoken query into SQL keywords. This proposed work will give the good results for simple and complex queries. 
* The accuracy of the system depends on the complexity of the database.
* This system will show that the voice-based user interface is an effective means of querying and fetching data from the stored database.
* Keywords: NLP, Speech, Speech to SQL, SQL, SQL generator, Synonym table. 

**Introduction:**

Speech recognition has become an essential part of a system with the fast growing technology. These interactive applications should be able to process the human communicating language queries. 
Natural Language Processing is the field of study that focuses on the interactions between human language and computers.
 It sits at the intersection of computer science, artificial intelligence, and computational. The spoken query
undergoes many steps to arrive at the final results.
Recent advances in voice-based interfaces, like Apple’s Siri, Google assistant. When used with database systems, voicebased interfaces provide an effective way to query and fetch data. 
A major advantage over classical query interfaces or even touch-based visual interfaces is that voice-based interfaces are completely hands-free.

**Literature Review:**

* Kumar et al. [6] proposed system which uses the knowledge ofunderlying database and generate lex file automatically, which will be used while tokenizing the words involved in English text query and since lex file contains underlying database
information like column and table names.
* So, automatic
generation of lex file helps in making the system database
independent. 
* In first phase of this work, speech is converted into
text, Second phase analyses the text whether it is syntactically
correct or not based on grammar rules for valid queries, In
third phase text is mapped into an intermediate query using
lexer, parser and syntax directed translation, In fourth phase
we extract the SELECT clause and WHERE clause from the
intermediate query, In fifth phase we find all the required tables
to form the FROM clause and thus SQL query is formed, In
sixth phase formulated SQL query is fired to database and result
is obtained. 
* This System has been checked for single tables and
multiple tables and it gives correct result if the input query is
syntactically consistent with the Syntactic Rules.
* Salma Jamoussi et al.[7] proposed statistical approach which
constitutes the most used method for resolving the speech
understanding problem. For this, they use a Bayesian network
for unsupervised classification, called Auto Class and we expose
three methods for the vector representation of words, these
representations aim to help the Bayesian network to build up
efficient concepts.
* We test this method on two applications data
and we compare the Bayesian network performances with those
obtained by the Kohonen maps and the K-means algorithm.
* Then, we will describe the last stage of our understanding
process, in which we label the user requests and we generate the 

**Model Architecture:**

 # System Design
* The system accepts the spoken query as its input and it is sent to
speech recognition engine, the output of that phase will be the
input text query which is in the mixed format. 
* The correct input
query is extracted and further sent to tokenisation. Tokenisation
is the method of splitting the sentence into individual words
and storing it in the list. Unwanted tokens are removed after
storing it in the list. 
* The tokens are mapped with the pre stored
synonym database which contains the words with its synonyms.
The refined text is then sent to text translator.
* Text translator
contains clause extractor and mapper. Through which an
intermediate query is being generated and tokens are mapped
with the table name and attribute.
* The result of this phase is
the SQL query. This SQL query is operated on the database and
correct results is being displayed on the interface.
* The SQL
query will be displayed on to the command prompt.In the system, multiple where clauses are also supported. Inner
join operation takes place. The primary and foreign keys are
compared to remove the redundant bits and correct result is
being obtained.

**Methodology:**

* Step 1. Accept the input from the user in the form of
speech.
* Step 2. The speech is converted into text by using speech
recognition engine.
* Step 3. The correct form of the statement is saved and
other statements are discarded.
* Step 4. Divide the input query and store it in a list, i.e.
tokenising the input query statement.
* Step 5. Remove the unnecessary token from the list like,
the, an, etc.
* Step 6. Map the tokens with the table name and attributes
of the database.
* Step 7. Now find the tables which will contain the pair of
((attribute which do not belong to the table in the query),
(other attributes present in the table in the query)).
* Step 8. For a natural join, find out the common attribute
and form the inner query. Then form the outer query according to the different conditions. Merge both of them
and generate the final query.
* Step 9. For a simple query, generate the final query by
checking the all conditions.
* Step 10. Obtain the conditions of the where clause and
other clause such as comparators, aggregate function and
relational operators, add these to the final query.
* Step 11. Print the final query on command prompt and
display results on UI..

**Results and Discussion:**

* The results are drawn based on the query execution rate. The
system is been tested on a college database containing 2, 3, 4
tables. 
* The interface is the voice based interface which allow
you to start speaking after a click on the button and ‘done’ is the
word to end the speech.
* The results are displayed on the UI and
the query is displayed on the command prompt.
* The system is tested for 3 different database varying from 2 to
4 tables.
* The efficiency of the system reduces as the number of tables
increases.
* The following types of queries are tested and results are being
listed,
∑ Type 1 - Simple query operation.
∑ Type 2 - Join operation with no condition.
∑ Type 3 - Join operation with multiple conditions.
∑ Type 4 - Join operation with comparators.
∑ Type 5 - Having and like clauses.
∑ Type 6 - Multiple Join with multiple where conditions.
The Table I gives the results of the college database containing
2 tables.


**Conclusion:**

Areas of improvement can be working on improving the
grammar in order to ensure that even the more general query
is being executed. Further we can work on DML like insertion,
deletion of tables and attributes and DDL like create, alter of
tables.

**References:**

* [1] J. Weizenbaum, “ELIZA - A computer program for the
study of natural language communication between man
and machine,” Communications of the ACM, vol. 9, no.
1, pp. 36-45, January 1966..
* [2]T. Winograd, “Procedures as a representation for data in
a computer program for understanding natural language,”
MIT AI Technical Report 235, February 1971.

* [3] B.-B. Huang, G. Zang, and P. C.-Y. Sheu, “A natural
language database interface based on probabilistic context free grammar,” IEEE International Workshop on
Semantic Computing and Systems, Huangshan, China,
14-15 July 2008.
* [4] G. G. Hendrix, E. D. Sacerdoti, D. Sagalowicz, and J.
Slocum, “Developing a natural language interface to complex data,” in ACM Transactions on Database Systems,
vol. 3, no. 2, pp. 105-147, June 1978.
* [5] N. T. Dang, and D. T. T. Tuyen, “Natural language question answering model applied to document retrieval
system,” World Academy of Science, Engineering and
Technology, vol. 51, pp. 36-39, 2009.

