import streamlit as st
import pickle
import pandas as pd
model=0
# Load the saved model
with open('model1.pkl', 'rb') as f:
    try:
        model = pickle.load(f)
    except Exception as e:
        st.write(e,type(e))

st.title("Student Performance Prediction System")

# User input
#feature1 = st.slider("Feature 1", 0.0, 10.0, 5.0)
A=float(st.slider("scaled",0.0,1.0,0.01))
B=st.slider("Studyhour",1,4,1)
C=st.slider("Attendance",60,100,1)
D=st.slider("health",0,1,1)
E=st.slider("InternetAccess",0,1,1)
F=st.slider("Region",0,1,1)
G=st.slider("D/H",0,1,1)
H=st.slider("Time",5,40,1)
I=st.slider("Parent's educated",0,1,1)
J=st.slider("class response",0,2,1)

st.write(type((A)))
'''
st.write(type((B)))
st.write(type((C)))
st.write(type((D)))
st.write(type((E)))
st.write(type((F)))
st.write(type((G)))
st.write(type((H)))
st.write(type((I)))
st.write(type((J)))'''
# Preprocess input (if necessary)
# ...

# Make prediction
if st.button("Predict"):
    # Assuming your model expects a DataFrame or specific input format
    input_data = pd.DataFrame([[A,B,C,D,E,F,G,H,I,J]], columns=['scaled','Study hours','Attendance','health','Internet Access','Region','D/H','Time',"Parent's educated",'class response'])
    prediction = model.predict(input_data)
    st.write(f"The prediction is: {prediction[0]}")



























