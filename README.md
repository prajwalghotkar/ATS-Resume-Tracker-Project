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
![Screenshot 2025-07-04 122450](https://github.com/user-attachments/assets/c66eb8f2-ee87-46f1-ab97-a9dc6b474857)
![Screenshot 2025-07-04 122349](https://github.com/user-attachments/assets/6d83db57-506f-4d0b-9f45-75be1392b280)


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

# code ------->

from dotenv import load_dotenv

load_dotenv()
import base64
import streamlit as st
import os
import io
from PIL import Image 
import pdf2image
import google.generativeai as genai

genai.configure(api_key=os.getenv("GOOGLE_API_KEY"))

def get_gemini_response(input,pdf_cotent,prompt):
    model=genai.GenerativeModel('gemini-pro-vision')
    response=model.generate_content([input,pdf_content[0],prompt])
    return response.text

def input_pdf_setup(uploaded_file):
    if uploaded_file is not None:
        ## Convert the PDF to image
        images=pdf2image.convert_from_bytes(uploaded_file.read())

        first_page=images[0]

        # Convert to bytes
        img_byte_arr = io.BytesIO()
        first_page.save(img_byte_arr, format='JPEG')
        img_byte_arr = img_byte_arr.getvalue()

        pdf_parts = [
            {
                "mime_type": "image/jpeg",
                "data": base64.b64encode(img_byte_arr).decode()  # encode to base64
            }
        ]
        return pdf_parts
    else:
        raise FileNotFoundError("No file uploaded")

## Streamlit App

st.set_page_config(page_title="ATS Resume EXpert")
st.header("ATS Tracking System")
input_text=st.text_area("Job Description: ",key="input")
uploaded_file=st.file_uploader("Upload your resume(PDF)...",type=["pdf"])


if uploaded_file is not None:
    st.write("PDF Uploaded Successfully")


submit1 = st.button("Tell Me About the Resume")

#submit2 = st.button("How Can I Improvise my Skills")

submit3 = st.button("Percentage match")

input_prompt1 = """
 You are an experienced Technical Human Resource Manager,your task is to review the provided resume against the job description. 
  Please share your professional evaluation on whether the candidate's profile aligns with the role. 
 Highlight the strengths and weaknesses of the applicant in relation to the specified job requirements.
"""

input_prompt3 = """
You are an skilled ATS (Applicant Tracking System) scanner with a deep understanding of data science and ATS functionality, 
your task is to evaluate the resume against the provided job description. give me the percentage of match if the resume matches
the job description. First the output should come as percentage and then keywords missing and last final thoughts.
"""

if submit1:
    if uploaded_file is not None:
        pdf_content=input_pdf_setup(uploaded_file)
        response=get_gemini_response(input_prompt1,pdf_content,input_text)
        st.subheader("The Repsonse is")
        st.write(response)
    else:
        st.write("Please uplaod the resume")

elif submit3:
    if uploaded_file is not None:
        pdf_content=input_pdf_setup(uploaded_file)
        response=get_gemini_response(input_prompt3,pdf_content,input_text)
        st.subheader("The Repsonse is")
        st.write(response)
    else:
        st.write("Please uplaod the resume")


🙋‍♂️
Prajwal Ghotkar
