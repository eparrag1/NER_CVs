# RoleMapper
Custom NER Model Technical Assignment Task

Package requirements (and versions used): <br>
Python 3.8.18 <br>
Pandas 2.0.3 <br>
Numpy 1.23.5 <br>
Matplotlib 3.7.2 <br>

This code cleans and prepares the Resume Dataset from Kaggle (https://www.kaggle.com/datasets/gauravduttakiit/resume-dataset), combined with the job skills dataset (https://www.kaggle.com/datasets/maneeshdisodia/employment-skills) in order to produce a dataset for training a custom NER (Named Entity Recognition) model to tag job skills in CVs and job descriptions.

This code performs the following steps:<br>
Cleaning:<br>
-Removing unwanted and special characters e.g. non-ascii characterrs, bullet points, \n, \r, etc.<br>
Annotations: <br>
-NER training datasets require annotations of the locations of the skills in the text - as it would be labour-intensive to tag these manaually (which would be the optimal solution), a list of employment skills from the Kaggle dataset (originating from LinkedIn) is used to search and annotate these words in the text <br>
-Some of these skills are multiple words <br>
-The search is done on all lowercase text with multiple word skills as appearing on the skills list are combined with an underscore, e.g. natural_language_processing <br>
-The original text before these edits is then put into the cleaned dataset, to preserve the cases and spaces <br>



