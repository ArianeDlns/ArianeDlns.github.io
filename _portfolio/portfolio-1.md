---
title: "Chatbot with Rasa for French presidential elections"
excerpt: "<br/>End of study project with a chatbot built with [Rasa](https://rasa.com/) for the French presidential election of 2022. The chatbot is able to answer questions about the candidates, the election, and the voting process. <br> <img src='/images/portfolio/chatbot_architecture.png' width='70%' height='70%'>"
collection: portfolio
---
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/) 
[![Open in Visual Studio Code](https://img.shields.io/badge/Editor-VSCode-blue?style=flat-square&logo=visual-studio-code&logoColor=white)](https://github.dev/ArianeDlns/chatbot-presidentielle2022/tree/main)
[![GitHub commit](https://badgen.net/github/last-commit/ArianeDlns/chatbot-presidentielle2022/main)](https://GitHub.com/ArianeDlns/chatbot-presidentielle2022/commits/main)
[![GitHub issues](https://badgen.net/github/open-issues/ArianeDlns/chatbot-presidentielle2022)](https://GitHub.com/ArianeDlns/chatbot-presidentielle2022/issues/)

**Watch out!** WIP  
{: .notice}

This project is my end of study project @CentraleSupélec for the French presidential election of 2022.   
It is a political chatbot built with [Rasa](https://rasa.com/) the image is dockerized and deployed on a VM.  
Source code is available on [GitHub](https://github.com/ArianeDlns/chatbot-presidentielle2022).   

See the example below:
<p align=center>
<img src='/images/portfolio/chatbot_exemple.png' width='60%' height='60%'>
</p>

The user interacts with the chatbot via Telegram, which sends the messages to the Rasa NLU via connectors, where it identifies the intent, and responds to the Rasa Core, according to stories and actions. The models used for the conversation were generated by the trainer module and then transferred to the bot; these models can be versioned and evolved between bots.

The chatbot is able to answer questions about the candidates, the election, and the voting process. It also has a FAQ section, where the user can find answers to the most common questions. The chatbot is able to answer questions about the candidates, the election, and the voting process. 

#### Demo version
[![Demo](https://img.youtube.com/vi/L-CWzZgm6-A/0.jpg)](https://www.youtube.com/watch?v=L-CWzZgm6-A)

#### References
[1] Y. Bang, N. Lee, E. Ishii, A. Madotto et P. Fung, [«Assessing Political Prudence of Open-domain Chatbots,»](https://arxiv.org/abs/2106.06157) CoRR, abs/2106.06157, 2021.  
[2] C. Greyling, [«Updated: A Comparison Of Eight Chatbot,»](https://cobusgreyling.medium.com/) 18 Août 2020. [En ligne]. Available: https://cobusgreyling.medium.com/updated-a-comparison-of- eight-chatbot-environments-7f57d4e2dc09.  
[3] T. Bocklisch, J. Faulkner, N. Pawlowski et A. Nichol, [«Rasa: Open Source Language Understanding and Dialogue Management,»](http://arxiv.org/abs/1712.05181) CoRR, abs/1712.05181, 2017.  
[4] J. Kuan, [«Making a Lightweight, Low-Cost Rasa Chatbot with NGINX,»](https://ttt.studio/blog/rasa-chatbot/) 7 Juillet 2020. [En ligne]. Available: https://ttt.studio/blog/rasa-chatbot/. [Accès le 30 mars 2021].  
[5] J.-P. Fauconnier, [French Word Embeddings](http://fauconnier.github.io), 2015.  
[6] S. Roller, E. Dinan, N. Goyal, D. Ju, M. Williamson, L. Yinhan, J. Xu, M. Ott, K. Shuster, E. M. Smith, Y.-L. Boureau et J. Weston, [«Recipes for building an open-domain chatbot,»](https://arxiv.org/abs/2004.13637) CoRR, abs/2004.13637, 2020.  
[7] T. Wolf, L. Debut, V. Sanh, J. Chaumond, C. Delangue, A. Moi, P. Cistac, T. Rault, R. Louf, M. Funtowicz et J. Brew, [«HuggingFace's Transformers: State-of- the-art Natural Language Processing,»](http://arxiv.org/abs/1910.03771) CoRR,, 2019, abs/1910.03771,.     