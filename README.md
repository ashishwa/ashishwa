import streamlit as st
import pandas as pd

# 1. वेबसाइट का टाइटल और हेडर सेट करना
st.set_page_config(page_title="Exam Tracker", page_icon="📊", layout="centered")
st.title("📊 भारत सरकारी परीक्षा ट्रैकर - 2026")
st.write("UPSC, SSC और अन्य सरकारी परीक्षाओं के डेटा का लाइव विश्लेषण।")

# 2. हमारा डेटा (जो हमने पिछले प्रोजेक्ट में बनाया था)
exams_data = {
    'परीक्षा का नाम': ['UPSC CSE', 'SSC CGL', 'BPSC', 'RRB NTPC'],
    'कुल सीटें': [1000, 8500, 800, 5000],
    'कट-ऑफ (%)': [47.5, 68.0, 52.3, 74.2]
}
df = pd.DataFrame(exams_data)

# 3. वेबसाइट पर डेटा टेबल दिखाना
st.subheader("📋 परीक्षाओं का मुख्य डेटा")
st.dataframe(df, use_container_width=True)

# 4. इंटरैक्टिव चार्ट बनाना (वेबसाइट पर ग्राफ दिखाना)
st.subheader("📈 सीटों का तुलनात्मक ग्राफ़")
st.bar_chart(data=df, x='परीक्षा का नाम', y='कुल सीटें')

# 5. साइडबार में एक फ़िल्टर लगाना
st.sidebar.header("फिल्टर ऑप्शन")
selected_exam = st.sidebar.selectbox("किसी एक परीक्षा को चुनें:", df['परीक्षा का नाम'])

# चुने गए परीक्षा का डेटा अलग से दिखान
exam_info = df[df['परीक्षा का नाम'] == selected_exam]
st.sidebar.write(f"**सीटें:** {exam_info['कुल सीटें'].values[0]}")
st.sidebar.write(f"**कट-ऑफ:** {exam_info['कट-ऑफ (%)'].values[0]}%")

ा
exam_info = df[df['परीक्षा का नाम'] == selected_exam]
st.sidebar.write(f"**सीटें:** {exam_info['कुल सीटें'].values[0]}")
st.sidebar.write(f"**कट-ऑफ:** {exam_info['कट-ऑफ (%)'].values[0]}%")
