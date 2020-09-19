<script>
import { createEventDispatcher } from 'svelte';
import Button from './Button.svelte';
 
 
var quizTop =   {
  Quizliste:[
   {
     Category: "Gemuese",
    Quiz:  [
    {
      question: "how many percent water are cucumber?",
      answers:["96%", "60%", "2%", "80%"],
      result: "1"
    },
    {
      question: "bananas are members of which family?",
      answers:["Berries", "Palm", "Cactus", "Grape"],
      result: "1"
      },
    {
      question: "strawberries are members of which family?",
      answers:["Rose", "Palm", "Cactus", "Grape"],
      result: "1"
    },
    {
      question: "how much DNA do humans share with bananas?",
      answers:["60%", "1%", "30%", "99%"],
      result: "1"
    },
    {
      question: "calorie for calorie broccoli contains more protein than..?",
      answers:["steak", "apple", "sugar", "coffee"],
      result: "1"
    },
    {
      question: "pistachios are actually..?",
      answers:["fruits", "roots", "nuts", "flowers"],
      result: "1"
    },
    {
      question: "how many percent of all hazelnuts end up in Nutella?",
      answers:["5%", "10%", "25%", "50%"],
      result: "3"
    }
    ]
    },

    {
    Category: "Fastfood",
    Quiz:  [
    {
      question: "how invented the sandwich?",
      answers:["Earl of sandwich", "Thomas Eddison", "Napoleon", "Queen Marry"],
      result: "1"
      },
      {
        question: "how many blévitas are eaten per year?",
        answers:["500 million", "1 million", "1 million", "3"],
        result: "1"
        },
          {
          question: "how many liter migros ice tea are consumed per year?",
          answers:["60 million", "10 million", "2 million", "30 million"],
          result: "1"
        },
          {
        question: "in the 1800's ketchup was used as..?",
        answers:["medicine", "poison", "food", "paint"],
        result: "1"
        }

      ]
    },

     {
        Category: "Milch",
        Quiz:  [
        {
          question: "when was chocolate seen the first time in bar form?",
          answers:["1910", "1510", "2010", "1987"],
          result: "1"
        },
      {
          question: "wie sait me?",
          answers:["hallo", "hoi", "hoi2", "hoi3"],
          result: "2"
      },
      {
        question: "what did the aztecs used chocolate for?",
        answers:["currency", "paint", "poison", "food"],
        result: "1"
      },
      {
        question: "where did french fries originate from?",
        answers:["belgium", "france", "usa", "uk"],
        result: "1"
      }
      ]
    }
]
};


  var quiz = quizTop.Quizliste;

//const quiz = JSON.parse('../../data/quizquestions.json');

 

 const dispatch = createEventDispatcher();

 export let prod_id;

	let question = 'hole von json';
 
  let anser_id;
  let a1 = "a1 von json hole";
  let a2 = "a2 von json hole";
  let a3 = "a3 von json hole";
  let a4 = "a4 von json hole";

 
 let  prod_category =  0;  
 let  prod_cat_name =  "Milch";
  let questionId = 0;
  let answerId = 0;
  let numberWins=0;

  function getQuestion(){
  //to do loop for next questionId
  for (var i = 0; i < quiz.length; i++){
  if (quiz[i].Category == prod_cat_name){
    question = quiz[i].Quiz[questionId%quiz[i].Category.length].question;
      a1 = quiz[i].Quiz[questionId%quiz[i].Category.length].answers[0];
      a2 = quiz[i].Quiz[questionId%quiz[i].Category.length].answers[1];
      a3 = quiz[i].Quiz[questionId%quiz[i].Category.length].answers[2];
      a4 = quiz[i].Quiz[questionId%quiz[i].Category.length].answers[3];
      
      answerId=quiz[i].Quiz[questionId%quiz[i].Category.length].result;
    
      break;
    }
  };
};
getQuestion();
 

	function handleAnswer(event) {
		let incomingId = event.detail.text;
    if(incomingId==answerId) { 
      questionId++;
      numberWins++;
      getQuestion();
    }else{
      dispatch('message', {
        text: numberWins,
        prod_id: prod_id
    });
  }
    
	}


</script>




<style>
	:global(body) {
		background-color: #f2eee2;
		color: #0084f6;
		transition: background-color 0.3s
	}
	:global(body.dark-mode) {
		background-color: #1d3040;
		color: #bfc2c7;
	}
</style>

<div class="component">
    <div class="row">
        <div class="col">
            <!-- Start: Basic Card -->
            <div class="card shadow mb-4">
                <div class="card-header py-3">
                    <h6 class="text-primary m-0 font-weight-bold">Product Quiz</h6>
                </div>
                <div class="card-body">
                 <h2>Question , {question}?</h2>
    
               
                <Button id=1 on:message={handleAnswer}>
                  {a1}
                </Button>

                <Button id=2  on:message={handleAnswer}>
                  {a2}
                </Button>

                <Button id=3  on:message={handleAnswer}>
                  {a3}
                </Button>

                <Button id=4  on:message={handleAnswer}>
                  {a4}
                </Button>
                
              </div>
            </div>
            <!-- End: Basic Card -->
        </div>
    </div>
</div>

