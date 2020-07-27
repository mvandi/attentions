<p align=center><i> <img src="https://user-images.githubusercontent.com/42150335/83960910-2ae89580-a8c9-11ea-956e-482485197629.png" width=500> </i></p>  
    
<p align=center><i> <img src="https://github.com/gentaiscool/end2end-asr-pytorch/raw/master/img/pytorch-logo-dark.png" height=20> <img src="https://img.shields.io/badge/License-MIT-lightgrey" height=20> </i></p> 
  
<p align=center> nlp-attention: Some Attention Implementation in PyTorch </p>
  
## Intro
  
`nlp-attentions` provides some attentions used in natural language processing using pytorch.   
these attentions can used in neural machine translation, speech recognition, image captioning etc...  
  
![image](https://user-images.githubusercontent.com/42150335/83331902-7bf9f780-a2d3-11ea-8f7e-172f55deef45.png)
  
`Attention mechanism` allows to attend to different parts of the source sentence at each step of the output generation.   
Instead of encoding the input sequence into a single fixed context vector, we let the model learn how to generate a context vector for each output time step.  
  
## Implementation list
  
|Name|Alignment score function|Citation|  
|---|---|---|  
|Additive|score(***s_t***, ***h_i***) = **v** tanh(**W**\[***s_t***;***h_i***\])|[Bahdanau 2015](https://arxiv.org/pdf/1409.0473.pdf)|  
|Dot-Product|score(***s_t***, ***h_i***) = ***s_t*** · ***h_i***|[Luong 2015](https://arxiv.org/pdf/1508.04025.pdf)|  
|Location-Aware|score(***s_t***, ***h_i***) = **w** tanh(**W*****s_t*** + **V*****h_i*** + ***b***)|[Chorowski 2015](http://papers.nips.cc/paper/5847-attention-based-models-for-speech-recognition.pdf)|    
|Scaled Dot-Product|score(***s_t***, ***h_i***) = ***s_t*** · ***h_i*** / **d_k**|[Vaswani 2017](https://arxiv.org/abs/1706.03762)|  
|Multi-Head|score(***Q***, ***K***, ***V***) = (head_1, ..., head_n) **W**|[Vaswani 2017](https://arxiv.org/abs/1706.03762)|  
   
## How To Use

* `Multi-head`
```python
B, L, H, T = 32, 3, 512, 131  # batch, num_layers, hidden_dim, seq_len
N_HEAD = 8

attention = MultiHeadAttention(H, N_HEAD)

# examples
input_var = torch.FloatTensor(B, 1, H)
hidden = torch.zeros(L, B, H)
value = torch.FloatTensor(B, T, H)

output, hidden = nn.LSTM(input_var, hidden)
context, attn = attention(output, value)
```
  
## Troubleshoots and Contributing
If you have any questions, bug reports, and feature requests, please [open an issue](https://github.com/sooftware/nlp-attentions/issues) on Github.  
or Contacts sh951011@gmail.com please.
  
I appreciate any kind of feedback or contribution.  Feel free to proceed with small issues like bug fixes, documentation improvement.  For major contributions and new features, please discuss with the collaborators in corresponding issues.  
  
## Citing
```
@github{
  title = {nlp-attentions},
  author = {Soohwan Kim},
  publisher = {GitHub},
  url = {https://github.com/sooftware/nlp-attentions},
  year = {2020}
}
```
