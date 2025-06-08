<h1 align="center"> Retrieval-Augmented Generation with Gradio and Groq API Key</h1>
<p align="center"> Natural Language Processing Project</p>

<div align="center">

<img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54">

</div>

### Name : Muhammad Nasywan Sulthan Muyassar Arhata
### Tech Stack : Python, Gradio, LangChain, HuggingFace Embedding, FAISS vector store

---

### 1. Analysis about how the project works
- The project is a simple application that allows users to upload a PDF file and ask questions about it using the Retrieval-Augmented Generation (RAG) technique. The application uses the Groq API Key to access the Groq API, which provides access to a large collection of documents and allows for the retrieval of relevant information from the documents.

### 2. Analysis about how different every model works on Retrieval-Augmented Generation
```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile", # Change the model in the code
        temperature=1.0
    )
```
- Model used : ```[llama-3.3-70b-versatile, deepseek-r1-distill-llama-70b, gemma2-9b-it]```

2.1 Analysis on ```llama-3.3-70b-versatile``` : 
```
File used : submarine-warfare-an-illustrated-history.pdf

Query : What is a submarine

Output : A submarine is a watercraft capable of operating underwater. It is a vessel that can dive and stay beneath the surface of the ocean for extended periods, allowing it to conduct various missions such as naval warfare, reconnaissance, and research. Submarines are typically equipped with specialized systems and equipment that enable them to operate in the underwater environment, including ballast tanks, propulsion systems, and life support systems. They can be powered by various means, including diesel-electric, nuclear, or air-independent propulsion systems. Submarines are used by navies around the world for a variety of purposes, including defense, attack, and surveillance.
```
- Analysis : 
    - The model provided a comprehensive and accurate definition of a submarine. It correctly identified key characteristics such as its ability to operate underwater, its purpose (naval warfare, reconnaissance, research), and its operational components (ballast tanks, propulsion, life support). The model also touched upon various propulsion systems and their global usage by navies. This output demonstrates a strong understanding of the query and the ability to synthesize relevant information from the provided file.

2.2 Analysis on ```deepseek-r1-distill-llama-70b``` : 
```
File used : submarine-warfare-an-illustrated-history.pdf

Query : What is a submarine

Output : <think>
Okay, so I need to figure out what a submarine is. Let me start by looking through the provided context. It seems like there's a lot about submarine history, their roles in different wars, and how they're used in naval warfare. 

From the context, it mentions that submarines are "a deadly weapon of naval warfare." That tells me they're used for combat. They talk about SSNs and SSKs, which I think are types of submarines. SSNs might be nuclear-powered attack submarines, and SSKs could be conventional submarines. 

The text also describes how submarines operate. It mentions that they can be fully submerged, which makes them hard to detect. There's a part about anti-submarine warfare (ASW) and the challenges in detecting them, especially when they're underwater. So, submarines are vessels that can operate underwater, making them stealthy and dangerous.

It also talks about the prestige of submarines and how they're seen as a deterrent. That suggests that submarines have a strategic importance beyond just combat—they can influence naval power dynamics. 

I also see mentions of different uses, like hunting other submarines or being part of task forces. They also discuss the evolution of submarines, from early models to modern nuclear ones, which shows they've been around for a while and have evolved over time.

So, putting this together, a submarine is a type of naval vessel that can operate underwater, used for various military purposes, including combat and deterrence. They come in different types, like nuclear and conventional, and have played significant roles in warfare throughout history.
</think>

A submarine is a type of naval vessel designed to operate underwater, utilized for various military purposes, including combat and deterrence. They come in different types, such as nuclear-powered attack submarines (SSNs) and conventional submarines (SSKs). Submarines have played significant roles in warfare throughout history, valued for their stealth and strategic importance.
```
- Analysis :
    - The model's output, including its thought process, shows a good analytical approach and ultimately provides a correct definition of a submarine. The thinking process demonstrates an effective strategy of identifying keywords, understanding the context of use (combat, deterrence), and recognizing different types of submarines (SSNs, SSKs). While the final output is concise and accurate, the detailed think section reveals a robust understanding of the document's content and how to extract the necessary information to answer the query.

2.3 Analysis on ```gemma2-9b-it``` : 
```
File used : submarine-warfare-an-illustrated-history.pdf

Query : What is a submarine

Output : This text describes submarines and their history in naval warfare. 

It does not say what a submarine is. 
```
- Analysis : 
    - The model failed to answer the query "What is a submarine." Its response indicates that it understood the document describes submarines and their history but incorrectly concluded that the text does not define what a submarine is. This suggests a lack of ability to synthesize information for a basic definition despite the information being present in the file. The model was unable to extract or infer a fundamental understanding of the subject from the provided context.

### 3. Analysis about how temperature works

```python
def get_llm():
    return ChatGroq(
        groq_api_key=GROQ_API_KEY,
        model_name="llama-3.3-70b-versatile",
        temperature=1.0 # Change the temperature value here and analzye
    )
```

3.1 Analysis on higher temperature 
```
Model used : llama-3.3-70b-versatile

Temperature : 2.0

Query : What is a submarine

Output : The text doesn't provide a clear, direct definition of a submarine. It focuses on submarine warfare, the role of submarines in naval warfare, and anti-submarine warfare. However, based on the content, it can be inferred that a submarine is a type of underwater vessel, likely a naval ship that operates beneath the surface of the water, used for military or naval purposes. If you'd like more information on submarines, I'd suggest looking elsewhere, as the given context doesn't provide a thorough explanation.
```
- Analysis : 
    - At a higher temperature (2.0), the model's performance degraded significantly compared to its previous output at temperature 1.0 (which was comprehensive and accurate). Instead of providing a direct definition, the model stated that the text "doesn't provide a clear, direct definition" and only offered an inference. While the inference is broadly correct (underwater vessel for military purposes), it lacks the detail and confidence of the previous output. This indicates that a higher temperature, intended to promote creativity and diversity, instead led to hesitation and a reduced ability to extract explicit information that was indeed present in the source material.

3.2 Analysis on lower temperature
```
Model used : llama-3.3-70b-versatile

Temperature : 0.0

Query : What is a submarine

Output : The provided text does not explicitly define what a submarine is. However, based on the context, it appears that a submarine is a type of naval vessel that operates underwater and is used for warfare. If you're looking for a more detailed definition, I don't have enough information to provide one.
```
- Analysis : 
    - At a lower temperature (0.0), the model also failed to provide a comprehensive definition, similar to the higher temperature output, and a stark contrast to its performance at temperature 1.0. It explicitly stated, "The provided text does not explicitly define what a submarine is," and offered only a very general inference. This suggests that at a very low temperature, which aims for more deterministic and focused output, the model became overly cautious and perhaps too literal in its interpretation, leading it to miss or downplay the implicitly available information within the text that would allow for a more complete definition.

### 4. How to run the project

- Clone this repository with : 

```git
git clone https://github.com/arifian853/RAG_with_GroqAPI.git
```

- Copy the ```.env.example``` file and rename it to ```.env```

```
GROQ_API_KEY=your-groq-api-key
```

- Fill the ```GROQ_API_KEY``` with your Groq API Key, find it here : https://console.groq.com/keys

- Set up a virtual environment and install dependencies. It's recommended to use a virtual environment to manage dependencies. Open your terminal or command prompt, navigate to your project directory, and follow these steps:

- Create the virtual environment:
```
python -m venv .venv
```
- Activate the virtual environment: 
```
.venv/bin/activate
```
- Install the required dependencies:
```
pip install -r requirements.txt 
```

- Run the application:
```
python app.py
```

- This will start the Gradio application. You'll typically see a local URL (e.g., http://127.0.0.1:7860) printed in your terminal. Open this URL in your web browser to access the UI.