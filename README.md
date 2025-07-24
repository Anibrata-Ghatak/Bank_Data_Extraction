# Bank Document Extractor – OCR + LLM (Mistral)
1. Abstract
The Bank Document Extractor is a lightweight web-based tool designed to automate the extraction of essential banking information—such as account holder name, account number, and IFSC code—from scanned passbook images. The system integrates Tesseract OCR for accurate text recognition and Mistral 7B LLM served via Ollama to extract structured data from unstructured text. The application is built using Gradio, offering a user-friendly front end. This solution enables fast, accurate, and low-cost bank data extraction for tasks such as KYC, loan applications, and financial onboarding.

2. Introduction
Bank passbooks contain key financial details that are often required in digital form. Manual transcription is time-consuming, error-prone, and inefficient. This project streamlines that process using OCR and AI. Unlike heavyweight enterprise systems, this implementation uses Tesseract for OCR and a lightweight Mistral model via Ollama to intelligently extract and format the data. The Gradio-based UI allows users to interact seamlessly, and public access via tools like LocalTunnel allows deployment even from restricted environments like Google Colab.

3. Objective
This system aims to:
Automatically extract key details from bank passbook images:
Account Holder Name
Account Number
IFSC Code

Improve efficiency by eliminating manual data entry
Enhance accuracy through LLM validation of OCR results
Output structured, readable text
Support real-time use with a simple web interface



4. Existing Approaches
Traditional OCR tools like Google Vision, AWS Textract, and Tesseract extract raw text but lack the semantic understanding required to identify bank-specific fields. Solutions like ABBYY or Adobe Acrobat also focus on layout and PDF conversion rather than structured, field-specific extraction. Most commercial tools are expensive, and open-source ones often require extensive post-processing.



5. Related Works
Tesseract OCR is widely used for open-source text extraction.
LLM-based extraction, like LayoutLM or Donut, requires heavy compute and complex deployment.
Hybrid systems (OCR + NLP) are being researched, but often lack lightweight, deployable implementations.
This project offers a minimal, fast, and deployable alternative using open-source OCR + LLM techniques.



6. Problems in Existing Tools
Domain-agnostic: They don’t understand banking contexts.
Complex deployment: Hard to use in lightweight or low-resource environments.
Unstructured outputs: Requires manual cleaning.
High cost: Many are paid services.
Limited real-time usability: Most are batch or desktop-based tools.




7. Proposed Methodology
Modules:
Image Upload (Gradio)
User uploads a passbook image.
OCR Processing (Tesseract)
Extracts raw text using Tesseract with optimized preprocessing (--oem 3 --psm 6).
Text Interpretation (Mistral LLM via Ollama)
LLM receives the OCR text and returns a structured dictionary containing:

"Account Holder Name"
"Account Number"
"IFSC Code"

Text Display (Gradio)
Extracted info is presented as clean, readable plain text.
Reset Option
A clear button resets the interface.
Public access via LocalTunnel can be added in Google Colab environments.



8. Results and Discussion
Tested on 20+ passbook samples with various lighting and fonts.

Achieved:
~91% accuracy in field identification
~87% structured formatting success


Common issues:
Blurred or cropped images reduce OCR accuracy
IFSC codes with typos (e.g., “O” vs “0”) handled well by LLM
Average processing time: ~15–20 seconds on Colab (4GB RAM)



OUTLOOK:
![image alt](https://github.com/Anibrata-Ghatak/Bank_Data_Extraction/blob/c0cd91dff8aefe886412dc332a17c1943a6a1978/Screenshot%202025-05-06%20130418.png)







                         
 
          
       




  

                             INPUT                                                         OUTPUT 
Output for bad Bank Passbook image:

![image alt](https://github.com/Anibrata-Ghatak/Bank_Data_Extraction/blob/6e9fa1d4466f506cf203c10c3d30f1b80738ba32/Screenshot%202025-05-07%20115215.png)











                            
                                 Input                                                         Output



10. Conclusion and Future Work
The Bank Document Extractor is a practical, lightweight solution that brings AI-powered extraction to banking workflows using entirely open-source tools. It reduces the effort and errors involved in handling bank documents and provides a user-friendly experience through Gradio.

🚀 Future Enhancements:

Add multilingual OCR (e.g., Hindi, Bengali)
Extend to PDF extraction
Include NER-based analytics
Add database/Excel export
Upgrade to Mixtral or GPT-J for smarter extraction




11. References:

Tesseract OCR
Ollama: Run Mistral locally
Gradio Documentation
Google Colab
LocalTunnel for public URLs
________________________________________
