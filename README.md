# auto_ml
A library package used to automate the machine learning on regression and classification problems.

"""The function data_summary() is used to provide a basic details of the 
       given tabular dataset.
       
       data_summary(data) function contains one argument.
       
       data -> We need to pass the entire dataframe to this function. (type = dataframe)
       
       Example: data_summary(data = dataframe_name)"""
       
       """The function data_eda() is used to provide a basic exploratory data analysis of the 
       given tabular dataset using matplotlib and seaborn library.
       
       data_eda(data, target_column_name, ml_type) function contains three argument.
       
       data -> We need to pass the entire dataframe to this function. (type = dataframe)
       target_column_name -> We need to pass the column name of the target variable (y). (type = string)
       regression -> We need to pass the supervised learning type based on the target_column_name. (type = bool)
                   True -> target_column is numerical.
                   False -> target_column is discrete or categorical.
       
       Example: data_eda(data = dataframe_name, target_column_name = column_name, regression = True)
                data_eda(data = dataframe_name, target_column_name = column_name, regression = False)"""
                
        """The function train_data_handling() is used to handle null values and outliers in the dataset.
       This function is only used for training dataset. Don't use it for test dataset.
       It seperates the given data into numerical data, discrete data and categorical data.
       
       For numerical data, the null values are filled based on the skewness of the data.
       For discrete and categorical data the null values are filled randomly based on their unique values.
       
       The outliers in numerical data are cured by quantile or percentile method by passing the value between 0.10 to 0.90.
       
       train_data_handling(data, file_to_dump, regression, target_column_name, min_outlier_fill, max_outlier_fill)
       This function contains six arguments.
           
           data -> We need to pass the entire train dataframe. (type = dataframe)
           file_to_dump -> We need to pass the file name to dump the handling_na_values and handling_outliers values for 
                           future use. (type = str)
           regression -> We need to pass the supervised learning type based on the target_column_name. (type = bool)
                   True -> target_column is numerical.
                   False -> target_column is discrete or categorical.
           target_colum_name -> We need to pass the column name of the target variable (y). (type = string)
           min_outlier_fill -> We need to pass the quantile value to replace the minimum outlier. (type = float or int)
                               range = 0.10 to 0.50
           max_outlier_fill -> We need to pass the quantile value to replace the maximum outlier. (type = float or int)
                               range = 0.50 to 0.90
                               
            This function will return a dataframe which has no null values and outliers.
            
            Example: train_data_handling(data = dataframe, file_to_dump = "file name", regression = True, target_column_name = column_name)
                     train_data_handling(data = dataframe, file_to_dump = "file name", regression = False, target_column_name = column_name,
                     min_outlier_fill = 0.45, max_outlier_fill = 0.85)"""
        
        """The function test_data_handling() is used to handle the null values and outliers
       on the test data based on the file created by the function train_data_handling().
       
       test_data_handling(data, na_file: str, outlier_file: str, regression: bool, min_outlier_fill = 0.10, max_outlier_fill = 0.90)
           This function contains six arguments.
           
           data -> We need to pass the entire train dataframe. (type = dataframe)
           na_file -> We need to pass the file name to load the handling_na_values to fill null values in test data. (type = str)
           outlier_file -> We need to pass the file name to load the handling_outliers values to replace outliers in test data. (type = str)
           regression -> We need to pass the supervised learning type based on the target_column_name. (type = bool)
                   True -> target_column is numerical.
                   False -> target_column is discrete or categorical.
           min_outlier_fill -> We need to pass the quantile value to replace the minimum outlier. (type = float or int)
                               range = 0.10 to 0.50
           max_outlier_fill -> We need to pass the quantile value to replace the maximum outlier. (type = float or int)
                               range = 0.50 to 0.90
                               
            This function will return a dataframe which has no null values and outliers.
            
            Example: train_data_handling(data = dataframe, na_file = "file name", outlier_file = "file name", regression = True)
                     train_data_handling(data = dataframe, na_file = "file name", outlier_file = "file name", regression = False, target_column_name = column_name,
                     min_outlier_fill = 0.45, max_outlier_fill = 0.85)"""
                     
        """The function data_corr() is used to get the correlation and p_value
       using spearman method.Because it can see both linear and non-linear data correlation.
       This function will neglect datetime columns present in the given data.
       It produce a dataframe for correlation and p_value and stored in the given file name
       
       data_corr(data, target_column_name, corr_file_name) contains three arguments.
           
           data -> We need to pass entire train dataframe. (type = dataframe)
           target_column_name -> We need to provide the column name of the target variable (y). (type = str)
           corr_file_name -> We need to pass a name to save the generated correlation dataframe. (type = str)
           
           This function will return a dataframe which does not contain any datetime column in the given dataframe.
           
           Example: data_corr(data = dataframe, target_column_name = "column_name", corr_file_name = "file_name")"""
           
     """The function data_encode_and_scale() is used to encode the categorical data 
       and scale the dataframe using standard scaler.
       
       If the test data is given in a dataframe this fuction will return two dataframe.
       
       data_encode_and_scale(data, test_data, target_column_name: str, correlation_file_name: str, confidence_level: int, file_name: str)
                             contains six arguments.
                             
                data -> We need to pass the entire dataframe. (type = dataframe)
                test_data -> We need to pass the test dataframe if available or any python object. (type = dataframe)
                target_column_name -> We need to provide the column name of the target variable (y). (type = str)
                correlation_file_name -> We need to pass the file that is generated by the function train_data_handling(). (type = str)
                confidence_level -> We need to pass an integer between 0 to 100 to get the p_value to select the features from dataframe. (type = int)
                file_name -> We need to pass a file name to save the encoding and scaling method to use in future.
                
        Example : data_encode_and_scale(data = "dataframe", test_data = "dataframe", target_column_name = "column_name", correlation_file_name: "correlation_file", confidence_level = 94, file_name = "file_name")
                    It will return a two dataframe which are scaled train dataframe and scaled test dataframe"""
    
    
     """The function train_model() is used to train the machine learning model
       for the given data.
       
       train_model(data, file_name: str, target_column_name: str, regression: bool) contains four arguments
       
           data -> We need to provide entire dataframe. (type = dataframe)
           file_name -> We need to provide the file name to save the model for future use. (type = str)
           target_column_name -> We need to provide the name of the target column name. (type = str)
           regression -> We need to provide a boolean data type whether the ml model is regression or classification. (type = bool)
           
           The function train_model() will return a dataframe that contains the information about the trained model.
           
               Example: train_model(data = dataframe, file_name = "file_name", target_column_name = "column_name", regression = True)
                        train_model(data = dataframe, file_name = "file_name", target_column_name = "column_name", regression = False)"""
    
    
     
    """The function test_model() is used to predict the target variable for the test data.
    
       test_model(data, test_data, train_file_name: str, target_column_name: str) contains four arguments
       
           data -> We need to provide the entire dataframe on which the train_model() is built. (type = dataframe)
           test_data -> We need to provide the test dataframe to predict the target variable. (type = dataframe)
           train_file_name -> We need to provide the any one train file name which is generated by train_model() function. (type = str)
           target_column_name -> We need to provide the target column name of the given data. (type = str)
           
           The function test_model() will return an array of predicted value for the given test data.
           
               Example: test_model(data = dataframe, test_model = test_dataframe, train_file_name = "file_name", target_column_name = "column_name")"""
 
