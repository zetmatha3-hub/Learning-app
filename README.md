import random
from datetime import datetime

questions = [
    {
        "question": "Which country has the largest population in Africa?",
        "options": ["A. Nigeria", "B. Egypt", "C. South Africa", "D. Kenya"],
        "answer": "A"
    },
    {
        "question": "What is the capital of Ghana?",
        "options": ["A. Accra", "B. Kumasi", "C. Tamale", "D. Cape Coast"],
        "answer": "A"
    },
    {
        "question": "Which desert is located in southern Africa?",
        "options": ["A. Sahara", "B. Kalahari", "C. Namib", "D. Gobi"],
        "answer": "B"
    }
]

def run_quiz():
    name = input("Enter your name: ")
    score = 0
    random.shuffle(questions)

    for q in questions:
        print("\n" + q["question"])
        for option in q["options"]:
            print(option)
        answer = input("Your answer (A/B/C/D): ").strip().upper()

        if answer == q["answer"]:
            print("✅ Correct!")
            score += 1
        else:
            print(f"❌ Wrong. Correct answer: {q['answer']}")

    print(f"\n{name}, your final score is {score}/{len(questions)}")

    # Save score with timestamp
    with open("africa_quiz_scores.txt", "a") as f:
        f.write(f"{datetime.now()} - {name}: {score}/{len(questions)}\n")

run_quiz()
