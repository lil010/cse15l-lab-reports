# Week 9 Lab Report

## Code lines in grade.sh

```
# Create your grading script here
set -e
CPATH=".:../lib/hamcrest-core-1.3.jar:../lib/junit-4.13.2.jar"
rm -rf student-submission
git clone $1 student-submission
cp TestListExamples.java student-submission
cd student-submission
SCORE=0
if [ -e "ListExamples.java" ]
then
    echo "ListExamples.java is found! 1 out of 3 points achieved."
    ((SCORE++))
else
    echo "Wrong file submission! Your score is " $SCORE"/3 unless you submit the file with correct name."
    exit
fi
javac -cp $CPATH *.java
if [ $? -ne 0 ]
then
    echo "File did not compile! Your score is " $SCORE"/3 unless you fix the compile error."
    exit
else
    echo "File successfully compiled! 2 out of 3 points achieved."
    ((SCORE++))
fi
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples &> testOutput.txt
if [ $? -eq 0 ]
then
    echo "Tests passed!"
    ((SCORE=SCORE+1))
    echo "Your score is " $SCORE"/3. Well done!"
    cat testOutput.txt
    exit
else
    echo "One or more of the tests didn't pass! Your score is " $SCORE"/3 until you pass all test."
    cat testOutput.txt
fi
```

I didn't successfully run through the server. My grade.sh does not compile with the server and I will fix it in resubmission. 