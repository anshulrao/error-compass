# Error Compass

Locate error messages closely matching the provided input from a mapping containing error messages paired with corresponding resolutions. This tool assists in directing users to the appropriate actions needed when encountering specific errors.


### MOTIVATION
The error messages in log files often follow a predictable pattern, as certain parts are hardcoded. When debugging an issue and encountering an error message, we typically follow a specific route to resolve it. However, if someone, whether a new team member or the same individual at a later time, encounters a similar error message, they may need to repeat the same troubleshooting process. This tool aims to address this challenge by storing information about previous resolutions, allowing users to search for and find the solutions previously taken.

### SUMMARY
We utilize this tool to collect all encountered errors along with the corresponding actions and resolutions. The INSERT panel facilitates this process by enabling us to record such information. Subsequently, whenever a user comes across an error in the logs, they can utilize the SEARCH panel to determine if that particular error or a similar one has been encountered previously. To enhance search accuracy, **cosine similarity** is employed to identify the top five closest errors stored in the file. The FILTER panel scans a log file to sift through all error or failure messages and then attempts to match and locate them in the file. The top five errors, ranked using the same cosine similarity logic, are displayed for each error message found in the log file.

#### COSINE SIMILARITY
Cosine similarity is a metric used to measure the similarity between two vectors in a vector space. It calculates the cosine of the angle between the two vectors, which gives an indication of how similar they are. In essence, two vectors in n-dimensional space are closer if the angle θ between them is small. This concept forms the fundamental principle behind this metric measurement.

$$\text{cosine similarity}(\mathbf{X}, \mathbf{Y}) = \frac{\mathbf{X} \cdot \mathbf{Y}}{\|\mathbf{X}\| \|\mathbf{Y}\|}$$

where:
- $\ \mathbf{X} \ and \ \mathbf{Y} \ are \ vectors \ in \ the \ same \ vector \ space.$
- $\( \cdot \) \ denotes \ the \ dot \ product \ of \ vectors \ \ \mathbf{X} \ and \ \mathbf{Y} \.$
- $\ \|\mathbf{X}\| \ and \ \|\mathbf{Y}\| \ denote \ the \ Euclidean \ norms \ (magnitudes) \ of \ vectors \ \ \mathbf{X} \ and \ \mathbf{Y} \ \ respectively.$

<br/>

  Example,
  
    Sentence 1: *"The cat sat on mat."*<br>
    Sentence 2: *"The dog sat on mat."*<br>
    Sentence 3: *"A bird flew over house."*<br>

    Now, let's convert these sentences into vectors based on word counts.<br>
    We'll consider a simple bag-of-words approach where each dimension of the vector<br>
    represents the count of a specific word in the sentence.

    Assuming a vocabulary of `["the", "cat", "sat", "on", "mat", "dog", "a", "bird", "flew", "over", "house"]`,<br>
    the vectors would be:

    S<sub>1</sub> = `[1,1,1,1,1,0,0,0,0,0,0]`<br>
    S<sub>2</sub> = `[1,0,1,1,1,1,0,0,0,0,0]`<br>
    S<sub>3</sub> = `[0,0,0,0,0,0,1,1,1,1,1]`<br>

    cosine_similarity(S<sub>1</sub>, S<sub>2</sub>) = `0.8`<br>
    cosine_similarity(S<sub>1</sub>, S<sub>3</sub>) = `0`<br>
    cosine_similarity(S<sub>2</sub>, S<sub>3</sub>) = `0`<br>


#### INSERT
<img width="1063" alt="Screenshot 2024-02-18 at 7 39 04 PM" src="https://github.com/anshulrao/error-compass/assets/31268509/f8fc8e68-5d2b-45c8-81cc-197fcfa81a20">


#### SEARCH
<img width="1064" alt="Screenshot 2024-02-18 at 7 50 26 PM" src="https://github.com/anshulrao/error-compass/assets/31268509/983b6eec-c53d-4825-ad4b-df6415ebaf79">


#### FILTER
<img width="1063" alt="Screenshot 2024-02-18 at 7 42 44 PM" src="https://github.com/anshulrao/error-compass/assets/31268509/a0b88114-f442-428e-b720-483d384ebf23">



