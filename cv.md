 My cv
## Junior Frontend developer
 ***

### Maryia Nedosekina
* Phone: +375291656948
* E-mail: maryia.leichenko@mail.ru
* Telegram: +375291656948
* Linkedln: Maryia Nedosekina
* Diskord: Maryia#3503
* GitHub: Maryia050

### About me
I worked for 7 years in the field of construction and design. My hobby was website design. I became interested in what is behind this picture, so I became interested in development.  I am studying to become a developer now. I can analyze large amounts of information well and quickly; good experience in solving non-standard situations; I quickly learn everything new. 

### Skills and Proficiency:
* HTML5, CSS3;
* JavaScript Basics;
* Java;
* Git, GitHub;
* VS Code, IntelliJ IDEA;
* Adobe Photoshop, Figma, SolidWorks.

### Languages:
+ Russian - Native;
+ English - Pre Intermediate;
+ Italian - Intermediate.

### Code project on GitHab
<https://github.com/Maryia050/rsschool-cv>

### Code example:
The code is written as a homework assignment when studying on the Way Up course
```//All answer options
const option1 = document.querySelector('.option1'),
    option2 = document.querySelector('.option2'),
    option3 = document.querySelector('.option3'),
    option4 = document.querySelector('.option4');

//All our options
const optionElements = document.querySelectorAll('.option');
    
const question = document.getElementById('question');//сам вопрос

const numberOfQuestion = document.getElementById('number-of-question'),//номер вопроса
      numberOfAllQuestions = document.getElementById('number-of-all-questions');//количество всех вопросов

let indexOfQuestion,//индекс текущего вопроса
    indexOfPage=0;//индекс страницы

const answersTracker = document.getElementById('answers-tracker'); //обертка для трекера
const btnNext = document.getElementById('btn-next');//кнопка далее

let score = 0; //итоговый рзультат викторины

const correctAnswer = document.getElementById('correct-answer'),//количество правильных ответов
      numberOfAllQuestions2 = document.getElementById('number-of-all-questions-2'), //количество вопросов в модальном окне
      btnTryAgain= document.getElementById('btn-try-again');//кнопка начать заново

const questions =
 [
    {
        question: 'В какой стране допускалось отправлять детей по почте?',
        options:[
            'США',
            'Перу',
            'Китай',
            'Италия',
                ],
        rightAnswer: 0
    },
    {
        question: 'Самая быстрая птица это -',
        options:[
            'Колибри',
            'Воробей',
            'Сапсан',
            'Курица',
                ],
        rightAnswer: 2
    },
    {
        question: '"2" + 2 =',
        options:[
            '4',
            '44',
            '22',
            '"2"2',
                ],
        rightAnswer: 2
    },
    {
        question: 'Как твои дела?',
        options:[
            'Отлично, сегодня лучший день в моей жизни',
            'Скорее всего мне снится страшный сон',
            'Бывало и лучше',
            'Живу',
                ],
        rightAnswer: 0
    }
];
         
numberOfAllQuestions.innerHTML = questions.length;//выводим колво вопросов
          
const load = () => {
    question.innerHTML=questions[indexOfQuestion].question; //сам вопрос
    //мапим ответы
    option1.innerHTML = questions[indexOfQuestion].options[0];
    option2.innerHTML = questions[indexOfQuestion].options[1];
    option3.innerHTML = questions[indexOfQuestion].options[2];
    option4.innerHTML = questions[indexOfQuestion].options[3];
    numberOfQuestion.innerHTML = indexOfPage + 1; //установка номера текущей страницы
    indexOfPage++; //увеличение индекса станицы
 };
            
 let completedAnswers = []//массив для уже заданных вопросов
const randomQuestion = () => {
    let randomNumber = Math.floor( Math.random()*questions.length);
    let hitDuplicate = false;// якорь для проверки одинаковых вопросов
        
    if (indexOfPage == questions.length) {
        quizOver()
        } else {
            if(completedAnswers.length > 0) {
            completedAnswers.forEach(item => {
                if(item == randomNumber) {
                hitDuplicate = true;
                }
            });
                if (hitDuplicate) {
                randomQuestion();
                } else {
                    indexOfQuestion = randomNumber;
                    load();
                    }
                 }
                    if(completedAnswers.length == 0) {
                        indexOfQuestion = randomNumber;
                        load();
                    }
                }
                completedAnswers.push(indexOfQuestion);
            };

const checkAnswer = el => {
    if(el.target.dataset.id == questions[indexOfQuestion].rightAnswer){
        el.target.classList.add('correct');
        updateAnswerTracker('correct');
        score++;
     } else {
        el.target.classList.add('wrong');
        updateAnswerTracker('wrong');
    }
    disabledOptions();
}
for(option of optionElements) {
    option.addEventListener('click', e => checkAnswer(e));
}

const disabledOptions = () => {
    optionElements.forEach(item => {
    item.classList.add('disabled');
    if(item.dataset.id == questions[indexOfQuestion].rightAnswer){
    item.classList.add('correct');
    }
})
}
//удаление всех классов со всех ответов
const enableOptions = () => {
    optionElements.forEach(item => {
        item.classList.remove('disabled','correct','wrong');
    })
}
const answerTracker = () => {
    questions.forEach(() => {
        const div = document.createElement('div');
        answersTracker.appendChild(div);
    })
}

const updateAnswerTracker= status =>{
    answersTracker.children[indexOfPage-1].classList.add(`${status}`);
}

const validate = () => {
    if(!optionElements[0].classList.contains('disabled')){
    alert('Вам нужно выбрать один из вариантов ответа');
    } else {
        randomQuestion();
        enableOptions();
    }
}

const quizOver = () => {
    document.querySelector('.quiz-over-modal').classList.add('active');
    correctAnswer.innerHTML= score;
    numberOfAllQuestions2.innerHTML = questions.length;

}

const tryAgain = () =>{
    window.location.reload();
}
btnTryAgain.addEventListener('click', tryAgain);

btnNext.addEventListener('click', () => {
    validate();
})

    window.addEventListener('load', () => {
              randomQuestion();
              answerTracker();
          }); ```
