
---
17th Oct 2024

**1. Maximize Reuse of In-House Library Functions**

- **Familiarity with In-House Tools**: Review end2endML project thoroughly to understand available functions before starting any new data processing task.
- **Minimize Duplication**: Before writing new code, ensure that similar functions are not already available in the library. If a function or utility partially meets your requirements, adapt your problem to it where possible.
- **Leverage Utility Functions**: Use high-level utility functions from the in-house library wherever possible to avoid unnecessary complexity. Check if pre-existing functions for data cleaning, transformation, or feature extraction can be leveraged before writing new ones.

**2. Write Generalizable Functions**

- **Avoid Hardcoding**: Ensure functions are flexible by using parameters instead of hardcoding values. This makes it easy to reuse functions across projects.
- **Parameterize Common Operations**: Make all common operations (like handling missing data, filtering, or normalization) configurable via function parameters to cater to different datasets and requirements.
- **Focus on Modularity**: Break down tasks into small, reusable functions. This encourages recombination for other projects and avoids redundant coding efforts.
- **Clear Input and Output Specifications**: Ensure that functions accept generic inputs (e.g., DataFrames, dictionaries) and produce well-documented, consistent outputs, which makes them easier to integrate into other projects.

**3. Documentation and Readability**

- **Docstrings**: Every function should have a docstring describing its purpose, input parameters, output, and potential exceptions. Emphasize the use of templates for consistency.
- **Usage Examples**: Provide small examples within the docstring to show how each function can be used, especially focusing on integration with other in-house functions.
- **Naming Conventions**: Use consistent, descriptive names that indicate the function's operation and purpose. Follow a standard naming convention for easier understanding across the team.

**4. Consistent Data Processing Workflow**

- **Pipeline Design**: Keep your data processing steps modular and chainable, encouraging reusability. Prefer writing functions that can easily integrate into larger pipelines.
- **Preprocessing Modules**: Group functions that perform similar tasks into modules—for instance, "Data Cleaning", "Feature Engineering", and "Normalisation". This allows team members to easily identify where to find or add new functions.
- **Error Handling**: Anticipate common data issues (e.g., missing values, type mismatches) and handle them gracefully in the code to avoid runtime errors when used in different contexts.

**5. Testing and Validation**

- **Unit Tests**: Write unit tests for every function you create, ensuring it works as expected with various edge cases. This helps with confidence when reusing functions across projects.
- **Test with Real Data**: Run tests using actual data from other projects to validate the generalizability of your functions.
- **Collaborate on Reviews**: Encourage code reviews within the team to improve generalizability and adherence to the standards.

**6. Best Practices for Data Handling**

- **Memory Efficiency**: Pay attention to data types and minimize memory usage when handling large datasets. Use in-house utilities for handling large data in chunks where possible.
- **Logging**: Use consistent logging to track data processing steps, especially for transformations that change data distributions.

**7. Model Training Using In-House Framework**

- **model\_trainer Object**: Use the in-house `model_trainer` object as a wrapper to build model blocks. This object reads in a configuration file and then builds a model based on it.
- **Configuration-Driven Models**: Ensure that model configuration details (e.g., hyperparameters, model type) are defined in configuration files to promote consistency and reproducibility across projects.
- **Integration with Data Processing**: Ensure data processing functions are designed to work seamlessly with `model_trainer`, allowing for easy integration into the model training pipeline.

By following these guidelines, the goal is to create a codebase that maximizes reusability, reduces redundancy, and ultimately makes future projects more efficient. Always remember to check the in-house library first—chances are someone has already done a part of the work for you.

