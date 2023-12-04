# Custom NER Model Technical Assignment Task

Package requirements (and versions used): <br>
* Python 3.8.18 <br>
* Pandas 2.0.3 <br>
* Numpy 1.23.5 <br>
* Matplotlib 3.7.2 <br>

This code cleans and prepares the Resume Dataset from Kaggle (https://www.kaggle.com/datasets/gauravduttakiit/resume-dataset), combined with the job skills dataset (https://www.kaggle.com/datasets/maneeshdisodia/employment-skills) in order to produce a dataset for training a custom NER (Named Entity Recognition) model to tag job skills in CVs and job descriptions.

## Data_Preparation_EleonoraParrag.ipynb <br>

This code performs the following steps:<br>
<br>
Cleaning:<br>
* Removing unwanted and special characters e.g. non-ascii characterrs, bullet points, \n, \r, etc.<br>


Annotations: <br>
* NER training datasets require annotations of the locations of the skills in the text - as it would be labour-intensive to tag these manaually (which would be the optimal solution), a list of employment skills from the Kaggle dataset (originating from LinkedIn) is used to search and annotate these words in the text <br>
* Some of these skills are multiple words <br>
* The search is done on all lowercase text with multiple word skills (as appearing on the skills list) combined with an underscore, e.g. natural_language_processing <br>
* The original text before these edits is then put into the cleaned dataset, to preserve the cases and spaces <br>

Output: <br>
 <br>
CSV with the following columns:
* Category (Type of job)
* Resume (original text)
* Cleaned_text
* indices (array of start and end indices for each skill word in the text)
* skill_words (list of skill words in the text)

  <br>

## Preparing_Input_Data.ipynb <br>
<br>
This output Cleaned_data.csv is ready to be converted to the format required by spaCy for input, e.g. 
<br>
{'label': 'SKILL', 'points': {'text': 'Programming Languages', 'start': 7, 'end': 28}} <br>
{'label': 'SKILL', 'points': {'text': 'python', 'start': 29, 'end': 35}} <br>
{'label': 'SKILL', 'points': {'text': 'Pandas', 'start': 36, 'end': 42}} <br>
{'label': 'SKILL', 'points': {'text': 'numpy', 'start': 43, 'end': 48}} <br>
<br>
This notebook reads in the Cleaned_data.csv and performs some formatting corrections (unfortunately when you save an array in Python it converts it to a string) <br>
Additionally, this code contains a function to convert a row of the dataframe into a dictionary ready for spaCy

