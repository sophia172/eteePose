
---
17th Oct 2024


### **1. Maximize Reuse of In-House Library Functions**

- **Familiarity with In-House Tools**: Review end2endML project thoroughly to understand available functions before starting any new data processing task.
- **Minimize Duplication**: Before writing new code, ensure that similar functions are not already available in the library. If a function or utility partially meets your requirements, adapt your problem to it where possible.
  - *Example*: If there is a function `inhouse_library.clean_data()`, adapt it for your specific needs instead of creating a new cleaning function.
- **Leverage Utility Functions**: Use high-level utility functions from the in-house library wherever possible to avoid unnecessary complexity. Check if pre-existing functions for data cleaning, transformation, or feature extraction can be leveraged before writing new ones.
  - *Example*: Use `inhouse_library.feature_extraction()` rather than writing your own extraction logic.

### **2. Write Generalizable Functions**

- **Avoid Hardcoding**: Ensure functions are flexible by using parameters instead of hardcoding values. This makes it easy to reuse functions across projects.
  - *Example*: Instead of hardcoding the threshold value, write `def filter_data(data: numpy.ndarray, threshold=0.5): ...`.
- **Parameterize Common Operations**: Make all common operations (like handling missing data, filtering, or normalization) configurable via function parameters to cater to different datasets and requirements.
  - *Example*: `def normalize_data(data, method='min-max'): ...` allows flexibility in choosing normalization techniques.
- **Focus on Modularity**: Break down tasks into small, reusable functions. This encourages recombination for other projects and avoids redundant coding efforts.
  - *Example*: Create separate functions like `def clean_data()`, `def transform_features()`, and `def split_data()` instead of having a single large function.
- **Clear Input and Output Specifications**: Ensure that functions accept generic inputs (e.g., DataFrames, dictionaries) and produce well-documented, consistent outputs, which makes them easier to integrate into other projects.
  - *Example*: `def process_data(input_df): return output_df` should clearly indicate what type of input and output is expected.

### **3. Documentation and Readability**

- **Docstrings**: Every function should have a docstring describing its purpose, input parameters, output, and potential exceptions. Emphasize the use of templates for consistency.
  - *Example*:
    ```python
    def clean_data(df):
        """
        Cleans the input DataFrame by removing NaN values.
        
        Parameters:
        df (pd.DataFrame): Input DataFrame to be cleaned.
        
        Returns:
        pd.DataFrame: Cleaned DataFrame.
        """
        ...
    ```
- **Usage Examples**: Provide small examples within the docstring to show how each function can be used, especially focusing on integration with other in-house functions.
  - *Example*:
    ```python
    def transform_data(df):
        """
        Transforms the input DataFrame by scaling numerical features.
        
        Example:
        df = transform_data(input_df)
        """
        ...
    ```
- **Naming Conventions**: Use consistent, descriptive names that indicate the function's operation and purpose. Follow a standard naming convention for easier understanding across the team.
  - *Example*: Use `normalize_features()` instead of a vague name like `norm_fn()`.

### **4. Consistent Data Processing Workflow**

- **Pipeline Design**: Keep your data processing steps modular and chainable, encouraging reusability. Prefer writing functions that can easily integrate into larger pipelines.
  - *Example*: Create functions that return DataFrames so they can be chained: `df = clean_data(df).pipe(transform_features).pipe(normalize_data)`.
- **Preprocessing Modules**: Group functions that perform similar tasks into modules—for instance, "Data Cleaning", "Feature Engineering", and "Normalisation". This allows team members to easily identify where to find or add new functions.
  - *Example*: Place `clean_data()` and `handle_missing_values()` in a "Data Cleaning" module.
- **Error Handling**: Anticipate common data issues (e.g., missing values, type mismatches) and handle them gracefully in the code to avoid runtime errors when used in different contexts.
  - *Example*: Add checks for NaN values and provide warnings: `if df.isnull().values.any(): logger.warning("Missing values detected.")`.

### **5. Testing and Validation**

- **Unit Tests**: Write unit tests for every function you create, ensuring it works as expected with various edge cases. This helps with confidence when reusing functions across projects.
  - *Example*: Use `pytest` to test `clean_data()` with different types of missing values.
- **Test with Real Data**: Run tests using actual data from other projects to validate the generalizability of your functions.
  - *Example*: Use a dataset from a different domain to test the `normalize_data()` function.
- **Collaborate on Reviews**: Encourage code reviews within the team to improve generalizability and adherence to the standards.
  - *Example*: Set up regular peer review meetings to discuss recent code contributions.

### **6. Best Practices for Data Handling**

- **Memory Efficiency**: Pay attention to data types and minimize memory usage when handling large datasets. Use in-house utilities for handling large data in chunks where possible.
  - *Example*: Use `inhouse_library.chunk_processor(df)` to process large datasets without memory issues.
- **Logging**: Use consistent logging to track data processing steps, especially for transformations that change data distributions.
  - *Example*: `logger.info("Scaling numerical features.")` before applying transformations.

### **7. Model Training Using In-House Framework**

- **model\_trainer Object**: Use the in-house `model_trainer` object to build models. This object reads in a configuration file and then builds a model based on it.
  - *Example*: `model = model_trainer(config_path='config/model_config.yaml')`.
- **Configuration-Driven Models**: Ensure that model configuration details (e.g., hyperparameters, model type) are defined in configuration files to promote consistency and reproducibility across projects.
  - *Example*: Define hyperparameters like learning rate in `model_config.yaml` rather than hardcoding them in the script.
- **Integration with Data Processing**: Ensure data processing functions are designed to work seamlessly with `model_trainer`, allowing for easy integration into the model training pipeline.
  - *Example*: `processed_data = process_data(input_data); model.train(processed_data)`.

### **8. Use in-house end2end ML library through pip installation**

```bash
pip install -v git+https://x-token-auth:ATCTT3xFfGN0k6pUEjdQuweqPL1qZ9weGf0dW6L6x6rYpgSpbOT_Lr9SeU6_BFDi81nyH-zKxPWs5O9xNbIRDTCSXcwI5nfP8B3YDcbk3ONTmYPp9Bmx0hg83rniphkkZdYM0H6GgpAgvuVXP2rIRUFiVOrbGqhwI0jKZvZANbQEqnveWzG2kRs=2A6E8DDC@bitbucket.org/tangi0/end2end-ml.git@colab
```

### **9. Add Simple Python Notebook to Showcase How to Use the New Functions**

- **Notebook Example**: Create a Jupyter notebook demonstrating the use of new functions for data processing and model training.

---
By following these guidelines, the goal is to create a codebase that maximises reusability, reduces redundancy, and ultimately makes future projects more efficient. Always remember to check the in-house library first—chances are someone has already done a part of the work for you.


