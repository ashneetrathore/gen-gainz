# :muscle: GENGAINZ

## :open_book: OVERVIEW
Date: May 2025\
Developer(s): Ashneet Rathore, Josephine Ligatsyah, Allison Yeh

GenGainz is a full-stack AI-powered web application that generates personalized workout routines based on user demographics (height, weight, age, etc.) and fitness preferences such as workout duration and targeted body groups. The app uses AWS services and was developed in a four-day span as a submission for the AWS CloudHacks hackathon hosted at UCI.

**Tech Stack** | Python, AWS Lambda, ExerciseDB API, Amazon Bedrock, React, Next.js, CSS, AWS Amplify

## :film_strip: DEMO
[Watch the demo on Youtube](https://youtu.be/xo7eef4Pw6g)

## :classical_building: ARCHITECTURE
> [!IMPORTANT]
> The AWS services for this project are no longer active. `workout_lambda.py` is included for reference. In production, it runs as a Lambda function hosted on AWS.

The backend is implemented in **Python** and runs entirely on **AWS Lambda**, and the frontend is built with **React + Next.js** and **CSS**. **AWS Amplify** was used for deployment and integration with AWS backend services.

Flow of a workout plan generation request:
- The user submits a form with demographic info and fitness preferences via the **React + Next.js** frontend
- The request triggers the **AWS Lambda** function, which calls the **ExerciseDB API** from RapidAPI to fetch relevant exercises
- Lambda constructs a prompt from the user input and fetched exercises, and sends it to **Amazon Bedrock**
- **Claude Sonnet** generates a personalized workout plan, which Lambda returns to the frontend for display 

## :open_file_folder: PROJECT FILE STRUCTURE
```bash
gen-gainz/
├── aws_lambda/         
│   └── workout_lambda.py          # Original AWS Lambda function (for reference purposes)
├── src/        
│   └── app/
│       ├── styles/                # Frontend CSS styles       
│       ├── workout/               
│       │   └── page.js            # Workout play display page
│       ├── layout.js              # Page layout structure
│       └── page.js                # Main app page and user input form 
├── public/                        # Static logos and icons
├── package.json                   # External dependencies
├── package-lock.json              # Locked dependency versions
├── jsconfig.json                  # JS config
├── next.config.mjs                # Next.js config
├── postcss.config.mjs             # PostCSS config
├── README.md                      # Project documentation
└── .gitignore                     # Ignored files
```