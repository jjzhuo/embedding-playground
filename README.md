<p align="center">
 <img src="https://i.ibb.co/pwxHR5X/default-3.png" alt="The Documentation Compendium"></a>
</p>

<h3 align="center">Embedding.store</h3>

<div align="center">

</div>

---
## Table of Contents

- [What is Embedding.store?](#what-is-embeddingstore)
- [How to use it?](#how-to-use-it)
  - [API details](#1-api-alpha---httpsapiembeddingstore)
  - [Playground UI](#2-playground-ui)
- [Embeddings](#embeddings)
  - [Request for datasets](https://airtable.com/shrp2Z0aQA4tSUtZC)
- [Get involved](#get-involved)
  - [Join Discord](https://discord.gg/hAnE4e5T6M)



## What is Embedding.store? 


## How to use it?

We are a developer-first product -- we are commited to building different methods for you to access our embeddings. Currently, you can access them into two ways -

### 1. API (alpha) - `https://api.embedding.store`
**Steps to get started**
1. Request for an [API key here](https://api.embedding.store/register)
2. Choose the dataset in which you want us to search the relevant contexts in ([check here](#embeddings) for available datasets)
3. Send us the prompt that you received from your user, along with a bunch of parameters ([check below](#retrieve) for more details)
4. The API will return the top k relevant embeddings with a set of data-specific metadata and retreival scores (similarity measures, etc.) 

Note : We will be actively updating and adding more features to the API. If you find a bug or want a new feature, let us know! 

##### `/retrieve`
**Sample code**
  ```python
  import requests
  url = 'https://api.embedding.store/retrieve'
  headers = {'API-Key': <YOUR_API_KEY>}

  # creating the payload
  payload = {"query": <PROMPT>,"dataset_params": {"dataset_id":"podcasts_01", "filters":{"category":["Business"]}}}

  response = requests.post(url, headers=headers, json=payload)

  # check the response
  print(response.json())
  ```

**Authorization**

Add the API key in the header : `{'API-Key'='<YOUR_API_KEY>'`

**Parameters**
| Param             | Details | Type  | Example
| ------------------- | ----------------------------- | -------- | ----------------------------- |
| query | the prompt on which contexts need to be retrieved  | `str`  | `What does Tim Ferris say about productivity?` |
| dataset_params | a dictionary of dataset specific parameters like dataset_id and filters  |  `dict` | `{"dataset_id":"podcasts_01", "filters":{"category":["Business"]}` |

By default, the API returns the top 3 contexts right now. We will be adding options to control this soon.

**Sample Response**
```json
{
    "success":"true",
    "contexts" : [
        {"episode_published_time": "2023-03-10T11:00:00Z", "episode_summary": "In this episode of My First Million, the hosts discuss a range of topics including making more money using what you already have, Elon Musk's recent controversies, a study on money and happiness, the potential ban of TikTok, and the emergence of the Power Slap League. They express skepticism towards the study on money and happiness and discuss the potential risks of TikTok. The hosts also express their disgust at the violence in the Power Slap League and recommend the Korean reality show Physical 100. ", "podcast_name": "My First Million", "speakers": ["the hosts"], "transcript_snippet": "to an extent. But I'm like, there's, but just because you say it like it is, like, well, he's just doing what he wants. Yeah, but he just, you just punched someone. Like, hitting people isn't good. Do you know what I mean? It's like, yeah, I want to do what I want. Does that mean I'm going to, like, go take a dump in the corner of the room? Like, you know, there's like, let's be polite to one another also, if possible. Right. We don't, we're not going to be needlessly, needlessly rude to one another. And that's kind of how I feel he acts right now. And that's not cool. Two other, two other parts of this news story. One, it's going around that this guy's payout was $100 million, which makes no sense. Anybody who's in business is like, well, that number makes no sense. There's no way he's getting paid $9 million a year of salary. There's no way that they bought his agency for $100 million. That's not how much you would acquire an agency for. It's probably more like 10. But it, and I"},
        {"episode_published_time": "2023-05-11T20:53:23Z", "episode_summary": "In this collection of podcast episode summaries, we learn that Lyft is discontinuing its pooled rides service, WhatsApp is tackling spam calls in India, and U.S. chip imports rose 13% in Q1 2023. Twitter launched encrypted direct messages for verified users, Peloton recalled 2.2 million bikes, and Disney lost streaming subscribers for the second quarter in a row. Disney is set to launch a single app for both Hulu and Disney Plus, while Fairphone has launched FairBuds XL, a pair of over-ear wireless noise-canceling headphones. The Daily Tech News Show discussed the new Asus Rogue Ally, a Windows-based handheld gaming device, and the disappointment of Google's Pixel tablet not being able to function as a home hub. They also talked about a recent Antiques Roadshow episode where a binder containing all 102 original base set Pokemon cards was appraised for a value of up to $10,000.", "podcast_name": "Daily Tech News Show", "speakers": ["The hosts", "Scott Johnson"], "transcript_snippet": "Steam Deck and you'll run your Steam games. It'll feel like a Steam Deck in many ways. But there is something nice about the Steam Deck's integration with the ecosystem that makes that a great experience if you're in that ecosystem, right. And a lot of gamers aren't. A lot of people are like, I don't want to be tied to Steam or Epic or anyone else. I want to have my games just loose on my hard drive and I want to install them the way I want to. That's always an option for most games still. Those people are going to be stoked about this. And that screen looks nice. Like there are a lot of good things to say but to answer your question more succinctly I think that battery life does matter and that will make a difference in the long run. So slimness is nice. Battery life is nicer. Well while you're enjoying battery life, maybe you're, I don't know, watching a television that runs on a battery. I don't know. But if you're not familiar with the long running TV series Antiques Roadshow, you"},
        {"episode_published_time": "2023-05-05T20:50:12Z", "episode_summary": "In this episode of Daily Tech News Show, the hosts discuss various technology-related news. Microsoft is reportedly collaborating with AMD to develop processors for AI workloads. 8BitDo has released a new wireless controller compatible with multiple devices. JBL's Tour Pro 2 buds have been released with a charging case featuring its own LCD display. Apple's earnings were unremarkable, but CEO Tim Cook confirmed the company's focus on AI. The hosts also discuss Grasp, a new search engine that allows users to create a customized search index based on websites they follow. They also predict what to expect from Google's upcoming I/O conference. The episode ends with a food technology quiz for patrons during the Good Day Internet segment.", "podcast_name": "Daily Tech News Show", "speakers": ["Tom Merritt", "Sarah Lane", "Roger Chang", "Rich Stroffolino", "Joe Kuntz", "Dan Campos", "Jen Cutter", "Dr. Nikki Ackermans", "Zoe Detterding", "Chris Ashley", "Nika Monfort", "Scott Johnson", "Justin Robert Young", "Shannon Morse"], "transcript_snippet": "the other products like the 7a, that one looks really interesting. I recently posted a video about comparing that to the Pixel 7 and how I probably wouldn't wait, especially since it's going to increase in price most likely to $500 while the 6a was $450. So you say jump on the 6a because it's cheaper? I would actually jump on the 7, even though it's a little bit more expensive. Yeah, because the tech is a little bit better. So that's just my personal opinion. I would love to see the tablet come out. Hopefully that does get announced, even though they haven't officially said anything. It's about time. I would be shocked if they don't announce it. It is about time, yes. I'm really curious if it's going to be another cheap Android tablet or if we've seen a few rumors about prices, but not a lot about the specs. So if it's a tablet that I could actually get some work done on, then I would seriously consider it because that would integrate very, very well into an Android content creator"}
    ]
}
```


### 2. Playground UI
We have created a [playground](https://playground.embedding.store/) for you to experiment with how adding relevant contexts affect the performance of the chatbot. 

## Embeddings

| Dataset             | Dataset Name (for API access) | Description | Status | More details |
| ------------------- | ----------------------------- | ------------------------------------------------------------- | ------ | ------------ |
| Podcast Transcripts | podcasts_01                   | 30 most recent podcasts across Finance, Business and Technology  | Live   | [Link](https://docs.google.com/spreadsheets/d/1F-MRI7Cqi0YXTsHxbdLEsq_qeXmhSx1qzPoqvW3MOQI/edit?usp=sharing)             |
| arXiv | arxiv_01                   |    -         | Coming Soon   |              |
| News | news_01                   |      -      | Coming Soon   |              |
 
## Get involved
We are early, and we want to know how you use our APIs and what else would you want to make the most out of the product. 

Join us on our [discord](https://discord.gg/hAnE4e5T6M), or feel free to email us at hello@embedding.store! 
