# cluster-novelty
The core of this algorithm lies in scoring the correlation between two different elements, in this case, clinical measurements, 
using information entropy. To calculate entropy, it is necessary to discretize the distribution of specific data. In this study, 
the research team investigated all reference values of clinical measurements used as the research subject and converted the values 
into binary form based on whether they deviate from the reference values.

Mutual information played a crucial role in the entropy computation. When two clinical chemical elements exhibit common clinical 
outliers or do not show them, they can be considered as co-occurrence. Conversely, if one element shows a clinical outlier while the other value 
remains within the reference range, it may appear as if one element is controlling the other clinical measurement (mutual exclusiveness). 
This algorithm takes both of these aspects into account to calculate the strength of correlation between two clinical measurements.

Subsequently, to determine if the calculated correlation score is statistically significant, data with similar characteristics 
to the input data was randomly generated. By using randomized data, randomized testing, and the Benjamini-Hochberg procedure, 
only statistically significant values with controlled false discovery rates, that is, p-values below 0.05, were derived.

In this study, based on the aforementioned methods, the interpretation was focused on the EIS (Entropy-based Information Scoring) values 
that were statistically significant, meaning they had a p-value below 0.05 in the FDR test.

(Please be patient. This repository is under construction.)

---
### Data preperation
In order to perform entropy-based calculations, it is necessary to convert all data into a discrete format. In this study, each clinical measurement 
was transformed into binary format, indicating whether it falls within the reference range or deviates from it, based on the reference values provided in the table below.

| Clinical Measurement | Variable Description | Reference Range |
| -------------------- | -------------------- | --------------- |
| PRT16_U | Urine(16)/Protein | 0 (negative) |
| GLU16_U | Urine(16)/Glucose | 0 (negative) |
| BLOOD16_U | Urine/Hematuria | 0 (negative) |
| HBA1C | Blood HbA1C | HbA1C < 5.6% |
| GLU0 | Blood Glucose | 70 - 99 (mg/dL) |
| BUN | Blood BUN | 6 - 20 (mg/dL) |
| ALBUMIN | Blood albumin | 3.5 - 5.2 (g/dL) |
| CREATINE | Blood creatinine | M: 0.70 - 1.20 (mg/dL)<br>F: 0.50 - 0.90 (mg/dL) |
| AST | Blood AST | M: 0 - 40 (IU/L)<br>F: 0 - 32 (IU/L) |
| T_BIL | Blood total bilirubin | 0.0 - 1.2 (mg/dL) |
| ALT | Blood ALT | M: 0 - 41 (IU/L)<br>F: 0 - 33 (IU/L) |
| TCHL | Blood total cholesterol | 0 - 199 (mg/dL) |
| R_GTP | Blood r-Gtp | M: 10 - 71 (IU/L)<br>F: 6 - 42 (IU/L) |
| HDL | Blood HDL cholesterol | 40 - 60 (mg/dL) |
| LDL | Blood LDL cholesterol | < 100 (mg/dL) |
| TG | Blood triglyceride | 0 - 149 (mg/dL) |
| WBC_B | Blood WBC | 4.00 - 10.00 (Thous/uL) |
| RBC_B | Blood RBC | M: 4.10 - 5.60 (Mil/uL)<br>F: 3.70 - 4.70 (Mil/uL) |
| HB | Blood Hemoglobin | M: 13.0 - 17.0 (g/dL)<br>F: 11.0 - 15.0 (g/dL) |
| HCT | Blood Hematocrit | M: 39.0 - 51.0 (%)<br>F: 33.0 - 45.0 (%) |
| PLAT | Blood Platelet | 150 - 370 Thous/uL |



---
### Python Packages Used

- Python (version 3.11)
    - Official Python website: [https://www.python.org/](https://www.python.org/)
- pandas
    - Wes McKinney. Data Structures for Statistical Computing in Python. Proceedings of the 9th Python in Science Conference, 2010. [https://doi.org/10.25080/Majora-92bf1922-00a](https://doi.org/10.25080/Majora-92bf1922-00a)
- pandarallel
    - Dennis O'Brien. pandarallel: A simple and efficient tool to parallelize pandas operations. Zenodo, 2019. [https://doi.org/10.5281/zenodo.3509134](https://doi.org/10.5281/zenodo.3509134)
- numpy
    - Harris, C.R., Millman, K.J., van der Walt, S.J. et al. Array programming with NumPy. Nature 585, 357–362 (2020). [https://www.nature.com/articles/s41586-020-2649-2](https://www.nature.com/articles/s41586-020-2649-2)
- tqdm
    - Casper da Costa-Luis. tqdm: A Fast, Extensible Progress Bar for Python and CLI. Zenodo, 2021. [https://zenodo.org/record/7697295](https://zenodo.org/record/7697295)
- networkx
    - Aric A. Hagberg, Daniel A. Schult, Pieter J. Swart. Exploring network structure, dynamics, and function using NetworkX. Proceedings of the 7th Python in Science Conference, 2008. [https://conference.scipy.org/proceedings/SciPy2008/paper_2/](https://conference.scipy.org/proceedings/SciPy2008/paper_2/)
- matplotlib
    - Hunter, J.D. Matplotlib: A 2D Graphics Environment. Computing in Science & Engineering, vol. 9, no. 3, pp. 90-95, 2007. [https://doi.org/10.1109/MCSE.2007.55](https://doi.org/10.1109/MCSE.2007.55)
- seaborn
    - Michael Waskom et al. mwaskom/seaborn: v0.11.2 (February 2021). Journal of Open Source Software, 6(60), 3021. [https://doi.org/10.21105/joss.03021](https://doi.org/10.21105/joss.03021)
- statsmodels
    - Josef Perktold, Skipper Seabold, Jonathan Taylor, statsmodels: Econometric and statistical modeling with python. Proceedings of the 9th Python in Science Conference, 2010. [https://conference.scipy.org/proceedings/scipy2010/pdfs/seabold.pdf](https://conference.scipy.org/proceedings/scipy2010/pdfs/seabold.pdf)

Please make sure to cite the relevant papers when using these packages if required by the research guidelines.

If you have any further questions or need additional assistance, feel free to ask!



