



# Live Speech to Text and Text to Speech 

> This respiratory is to convert the speech to text and vice versa by using [IBM WATSON](https://cloud.ibm.com) and [Python](https://www.python.org/downloads/) language.

![unnamed](https://user-images.githubusercontent.com/66702376/125099767-0b7df680-e0e1-11eb-9d98-f6cf0a0e8ff9.png)



## Built With

- Python language
- Speech to text IBM WATSON
- Text to Speech IBM WATSON



## 🦾 Getting Started
To get a local copy up and running follow these simple steps.

### Prerequisites
* [Python](https://www.python.org/downloads/)
* Account in [IBM Cloud](https://cloud.ibm.com)

### Setup
* Setup Watson STT Service: cloud.ibm.com/catalog 
  * Speech to Text. 
  * Text to Speech.
* Clone Live STT Code: https://github.com/IBM/watson-streaming-stt 

### Install
```
pip3 install pyaudio
pip3 install websocket-client
``` 

### Speech to Text 
* In [speech.cfg](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/speech.cfg) file
``` 
apikey = 'YD3YBUw2Cv3CRQUZ7OGDzLpXNy-5HIr9LtSEV2OrCXAZ' #Your apikey
```
* Create [output.text](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/output.txt) file by writing this code below in [transcribe.py](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/transcribe.py) file.
```
with open('output.txt', 'w') as out:
            out.writelines(data['results'][0]['alternatives'][0]['transcript'])
```
> inside the on_message function. 


### Text to Speech
* In [transcribe.py](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/transcribe.py) file write the code: 
```
authenticator = IAMAuthenticator('vYI9rkcSWl_wELYNt2Y-5uxAuNDmPKL9XkMLal4R0Vn1') #Your apikey
tts = TextToSpeechV1(authenticator=authenticator)
tts.set_service_url('https://api.us-south.text-to-speech.watson.cloud.ibm.com/instances/4afce834-c1d1-4edf-ba89-dafcd89544a0') #Your url
```
* Create [output.mp3](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/output.mp3) file write the code 
```
with open('output.txt', 'r') as f:
            text = f.readlines()
    text = [line.replace('\n','') for line in text]
    text = ''.join(str(line) for line in text)
    with open('./output.mp3', 'wb') as audio_file:
        res = tts.synthesize(text, accept='audio/mp3', voice='en-GB_JamesV3Voice').get_result()
        audio_file.write(res.content)
```
> inside the read_audio function. 








## 📝 Sources 

- [smart methods youtube video](https://www.youtube.com/watch?v=Z_N2aAHfiGU&t=5229s)
- https://www.youtube.com/watch?v=8k8S5ruFAUs&t=602s
- https://www.youtube.com/watch?v=A9_0OgW1LZU&t=310s
- https://www.youtube.com/watch?v=YCyuZM454_I&t=849s



