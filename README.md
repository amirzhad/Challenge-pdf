**Problem**:

A well-formed pdf file should end with a line starting with '%% EOF' (with sometimes, rarely, spurious bytes after this mark).
The object of the exercise is to quickly determine the offset in the file of the last occurrence of the 'line' starting with '%% EOF'. The offset is the index in bytes in the file of the first character, or -1 if the file does not contain an occurrence.
(The objective is to taking as argument the path to the pdf file to analyze, and displaying the offset in decimal on the standard output (-1 if there is no "%%EOF")).

**Run Instruction**:

To run the code you can easily use Jupyter Notebook or simply run the script in command line by "ipython netheos_amir.ipynb" (you have to have installed ipython)

**Solution**:
1) Instead of reading the whole file, I read from the end of the file. I read until I reach the "\n" or "\r" to find the last line. This way is efficient, especially for large files.
2) The max_reading_bytes defines the maximum number of character we will read from the end of the file. Each character can be from 1 to 4 bytes and I assumed that it is 1 (no difference in complexity of the method). If we read more than 30 bytes then it means that the last line does not contain "%%EOF" and we have to terminate the searching. This is done by checking the variable sum_of_read_bytes.
3) At the end, I will read the line (which is the last line) and then I check if it contains "%%EOF" or not.
4) Using the size of the file and the number of characters we read from the end, we can easily compute the offset (using size_of_file and sum_of_read_bytes).
