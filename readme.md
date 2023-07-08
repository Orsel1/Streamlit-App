  # How to Deploy Machine Learning Models Using Streamlit
## Introduction
Streamlit is a Python library that makes it easy to create interactive web apps for machine learning models. It is a great way to deploy your models to production, as it does not require any prior knowledge of web development.

In this article, I will show you how to deploy a machine learning model using Streamlit. I will assume a model that predicts store sells of a group of stores in Ecuador, the same principles can be applied to any machine learning model.
You can find the jupyter notebook and the python script for the original project [here](RegressionPipeline.ipynb) but for the sake of this article I will assume a simple dataset.

### 1. Prepare your model

The first step is to prepare your model. After training and evaluating several model on the training data set, you can save the model to be used in your streamlit app.  This means saving it to a file that Streamlit can read. A typical workflow in machine learning may include the following;

- Get Data
- Clean/preprocess/transform
- Train several models
- Evaluate and optimize the best model
- Clean/proprocess and transform new data
- fit machine learning model on new data to make prediction
  
You can make the above steps more easier by using the scikit learn pipeline class then using the pickle library in Python to export your final model. This final model may have pipeline containing encoders, imputers, scalers and the final estimator for encoding, handling missing values and scaling unbalanced datasets and the model to be fitted on the dataset.

```python
# sample code to export model using pickle
import pickle


pickle.dump(model, open(filename, 'wb'))


# sample code to load a pickle file


model = pickle.load(open('model.pkl', 'rb'))
```

### 2. Create a Streamlit app

Once you have your model saved, you can create a Streamlit app. This is a simple Python file that defines the user interface for your app.

```python
import streamlit as st
import pandas as pd

def main():
    # Get the input data from the user
    feature1 = st.number_input('x1')
    feature2 = st.number_input('x2')
    df = pd.DataFrame({"feature1":[feature1],"feature2":[feature2],})

    # Make a prediction
    prediction = model.predict(df)

    # Display the prediction to the user
    st.write('The predicted price is', prediction)

if __name__ == '__main__':
    main()
```

### 3. Deploy your app

Once you have created your Streamlit app, you can deploy it to production. There are a few different ways to do this, but the easiest way is to use Streamlit Share.

Streamlit Share is a free service that allows you to deploy your Streamlit apps to the internet. To use Streamlit Share, you simply need to create an account and upload your app.

Once your app is uploaded, you will be given a URL that you can share with others. Anyone who visits this URL will be able to run your app.

### Conclusion

Deploying machine learning models using Streamlit is a simple and easy way to make your models accessible to others. By following the steps in this article, you can deploy your models to production in a matter of minutes.

Here are some additional resources that you may find helpful:

* Streamlit documentation: https://docs.streamlit.io/en/stable/
* Streamlit Share: https://share.streamlit.io/
* Deploying Machine Learning Models with Python and Streamlit: https://365datascience.com/tutorials/machine-learning-tutorials/how-to-deploy-machine-learning-models-with-python-and-streamlit/

