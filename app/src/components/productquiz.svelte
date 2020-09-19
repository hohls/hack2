<script>
import { createEventDispatcher } from 'svelte';
import Button from './Button.svelte';

import prod_id_gl from './animation.svelte';
 
 
var quiz =   {
  "Quizliste":[
   {
     "Category": "Gemuese",
    "Quiz":  [
      {
        "question": "wie sait me?",
        "answers":["hallo", "hoi", "hoi2", "hoi3"],
        "result": "1"
      },
      {
        "question": "wie sait me?",
        "answers":["hallo", "hoi", "hoi2", "hoi3"],
        "result": "1"
      }
    ]
    },
    {
    "Category": "Mehl",
    "Quiz":  [
        {
          "question": "wie sait me?",
          "answers":["hallo", "hoi", "hoi2", "hoi3"],
          "result": "1"
        },
        {
          "question": "wie sait me?",
          "answers":["hallo", "hoi", "hoi2", "hoi3"],
          "result": "3"
        }
      ]
    },
      {
        "Category": "Milch",
        "Quiz":  [
        {
          "question": "wie sait me?",
          "answers":["hallo", "hoi", "hoi2", "hoi3"],
          "result": "1"
        },
        {
          "question": "wie sait me?",
          "answers":["hallo", "hoi", "hoi2", "hoi3"],
          "result": "2"
        }
      ]
    }
]
};
  

//const quiz = JSON.parse('../../data/quizquestions.json');

 

 const dispatch = createEventDispatcher();

 export let prod_id;

	let question = 'hole von json';
  let user_answer = -1;
  let anser_id;
  let a1 = "a1 von json hole";
  let a2 = "a2 von json hole";
  let a3 = "a3 von json hole";
  let a4 = "a4 von json hole";


	prod_id = 10; // event.detail.prod_id;
  prod_category =  0;  
  prod_cat_name =  "Mehl";

  for (var i = 0; i < quiz.length; i++){
  if (quiz[i].Category == prod_cat_name){
      a1 = quiz[i].Quiz.answers[0];
      a2 = quiz[i].Quiz.answers[1];
      a3 = quiz[i].Quiz.answers[2];
      a4 = quiz[i].Quiz.answers[3];
      
      question = quiz[i].Quiz.question;
      user_answer = quiz[i].Quiz.result;
      
    }
	};
 

	function handleAnswer(event) {
		var answer_id = event.detail.id;
    if(1) {//user_answer == answer_id){
         dispatch('message', {
        text: 'win',
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
                 <h2>Question 1, {question}?</h2>

              
               
                <Button on:message={handleAnswer}>
                  {a1}
                </Button>

                <Button on:message={handleAnswer}>
                  {a2}
                </Button>

                <Button on:message={handleAnswer}>
                  {a3}
                </Button>

                <Button on:message={handleAnswer}>
                  {a4}
                </Button>
                
              </div>
            </div>
            <!-- End: Basic Card -->
        </div>
    </div>
</div>

