# ATS Resume Tracker Project
# 🧠 ATS Resume Expert — Streamlit App Powered by Gemini Vision API

This project is an AI-powered ATS (Applicant Tracking System) Resume Scanner built with Streamlit and Google Gemini-Pro Vision API. It analyzes resumes (in PDF format) against job descriptions and evaluates the alignment using LLMs. This tool can help candidates understand how well their resume matches a given job description and how to improve it.

# 🚀 Features
✅ Upload your resume in PDF format

✅ Enter any job description

✅ Get a professional-level evaluation of your resume from an AI acting as an HR expert

✅ Get a percentage match score with missing keywords and final feedback

✅ Powered by Gemini-Pro Vision (Google's multimodal AI model)

✅ Beautiful Streamlit interface

# 🛠️ Tech Stack
## * Python

## * Streamlit – for the web interface

## * Google Generative AI (Gemini-Pro Vision) – for intelligent resume screening

## * pdf2image – to convert PDF to image

## * PIL – image processing

## * dotenv – secure API key management

# 📷 Screenshots
Add screenshots of the app UI here for visual appeal.
![prajwaldata2](https://github.com/user-attachments/assets/0c9886ad-f001-439c-84ac-509fc9032a4b)

![prajwaldata](https://github.com/user-attachments/assets/344b7bfa-d11b-4978-b6d1-3cc475c2348f)



# 🔧 Setup Instructions
#### 1) Clone the repository
C:\Users\pm\Desktop\ATS Resume Tracker\venv

#### 2) Create a virtual environment & install dependencies
pip install -r requirements.txt
##### * streamlit
##### * google-generativeai
##### * python-dotenv
##### * pdf2image

#### 3) Set up your .env file
##### ---> Create a .env file in the root directory and add your Google API key:
#### > GOOGLE_API_KEY=your_google_generativeai_api_key

#### 4) Run the Streamlit app
##### > streamlit run app.py

# 💡 How It Works

#### * When you upload a resume (PDF), it is converted to an image.

#### * Gemini-Pro Vision reads the resume image and job description.

#### * Based on your selected button, it either:

#####   ----> Gives professional HR feedback, or

#####   ----> Returns a match percentage, missing keywords, and improvement advice.

# 📈 Future Improvements

#### * Add multi-page PDF support

#### * Include skill suggestions using external APIs

#### * Store user uploads for version comparison

#### * Add visual resume scoring dashboard


 http://192.168.1.2:8501

🙋‍♂️
Prajwal Ghotkar
