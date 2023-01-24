# 30 days automate the boring staff with Python

## Day 1: Generating random quiz files
The lesson today is to generate 35 different quiz files with 50 different questions about capital of states. The code is below:
for quizNum in range(35):
    quizfile = open('quizfile%s.txt' %(quizNum+1), 'w')
    ansfile = open('quiz_answer%s.txt' %(quizNum+1), 'w')
    quizfile.write('Date:\n\nName:\n\n')
    quizfile.write((' ')*20 + 'Capitals Quizs (Form %s)' %(quizNum+1))
    quizfile.write('\n\n')
    state_list = list(capitals.keys())
    random.shuffle(state_list)
    for questionNum in range(50):
        correctanswer = capitals[state_list[questionNum]]
        wronganswers = list(capitals.values())
        del wronganswers[wronganswers.index(correctanswer)]
        wronganswers = random.sample(wronganswers, 3)
        answeroptions = wronganswers + [correctanswer]
        random.shuffle(answeroptions)
        quizfile.write('%s. What is the capital of %s?' %(questionNum+1, state_list[questionNum]))
        for i in range(4):
            quizfile.write('    %s. %s\n' %('ABCD'[i], answeroptions[i]))
        quizfile.write('\n')
        ansfile.write('%s. %s\n' %(questionNum+1, 'ABCD'[answeroptions.index(correctanswer)]))
    quizfile.close()
    ansfile.close()
