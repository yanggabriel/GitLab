# Quiz questions

This is only a "quiz" in the loosest sense that it's asking questions whose
answers will be part of your grade. Please use *any resources you want*, as
long as you list those resources (e.g. peers, websites, etc.)

## Navigating logs

1. What is the SHA for the last commit made by Prof. Xanda on the branch
xanda_0000_movie_processing?
(For this and future questions, the first 5 characters is plenty - neither
Git nor I need the whole SHA.)
Answer: d0fc8

2. What is the SHA for the last commit associated with line 9 of this file?
Answer: b2ed3

3. What did line 12 of this file say in commit d1d83?
Answer: 2. I should really finish writing this.

4. What changed between commit e474c and 82045?
Answer: 
Changed the line of gross_sort = lambda x : x["Gross"] to gross_sort = lambda x : int(x["Gross"]).
Also changed the line top_five = rows[:-5:-1] to top_five = rows[:-6:-1]



## Predicting merges

Assume at the start of each of these three questions that your
branch for switching to a top-10 list was called `top_ten`
and your branch generalizing to any number of movies was called `top_N`.
Predict the behavior of these three possible operations - you don't
have to provide a full `diff` but you should describe at a high level
what changes would happen.

These questions are supposed to be separate paths, not cumulative;
for example, you should *not* assume that the operations of 5 were run
before 6. When testing outcomes later in the lab, you should make sure to
revert back to the state of the branch before you started these questions.

5. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git merge top_N
```
Answer: git checkout test would allow you to navigate to a branch called test. Now that you are at test,
git merge top_N would merge/combine top_N back into the original branch of test. Branch test should
have the updated changes from top_N.


6. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout top_ten
git merge test
```
Answer: git checkout top_ten would allow you to navigate to a branch called top_ten. Now that you are at top_ten,
git merge test would merge/combine test back into the original branch of top_ten. Branch top_ten should have 
the updated changes from test.


7. What do you think would happen if you ran the following commands?
What branches would change, and how?
```
git checkout test
git rebase top_ten
git rebase top_N
```
Answer: git checkout test would allow you to navigate to a branch called test. Now that you are at test, 
git rebase top_ten command should rebase the changes from the top_ten branch into the current branch, which is test.
git rebase top_N command should rebase the changes from the top_N branch into the current branch, which is also test.
There is a merge conflict that I would resolve, because essentially the test branch would not know which changes are the correct
changes to make. For example, in the process_movie_data.py file, top_ten would call the top ten movies, and top_N would call
the top N movies. Therefore, because the test branch has the original call top 5 movies, it would not know which one to
switch to. After resolving the merge conflict, then we can continue the rebase and everything works out as intended.