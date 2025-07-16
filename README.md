# Estimativa da geração instantânea (nowcasting) de painéis solares a partir de imagens do céu

 O presente repositório foi criado para documentar os resultados do projeto final da disciplina de Aprendizado de Máquina do Professor Danilo Silva da Universidade Federal de Santa Catarina.
 O trabalho foi feito por mim, Gustavo, com auxílio do professor Danilo durante o semestre de 2025/1.

## Introdução

A previsão de curto prazo da geração solar é um grande desafio devido à alta volatilidade das condições meteorolóigcas. Dentre um dos fatores de maior influência na geração, está a cobertura das nuvens: em dias parcialmente nublados, por exemplo, a geração dos painéis pode cair a valores próximos de zero em questão de minutos. Dessa forma, este projeto explora o uso de imagens do céu para prever a geração instantânea (nowcasting) de painéis fotovoltaicos, utilizando Redes Neurais Convolucionais (CNNs), de forma a extrair informações complexas que modelos tradicionais não conseguem capturar.

Neste trabalho, duas arquiteturas de CNN foram implementadas e avaliadas:

- A arquitetura SUNSET, proposta por Sun et al. em [[1]](#1), utilizada como nosso baseline.
- Uma ResNet50V2 pré-treinada, que passou por um processo de fine-tuning para comparar seu desempenho com o modelo de referência.

O dataset utilizado no projeto pode ser encontrado em [[4]](#4). 

**OBS**: Para informações detalhadas sobre a metodologia adotada nos experimentos, bem como os códigos utilizados, consultar o [relatório do projeto](Relatorio-Projeto-Final-EEL7513-Gustavo-F-Bento.pdf) e o [notebook jupyter](solar_nowcasting_using_cnns.ipynb) onde foi feito todo o desenvolvimento.


## Resultados Gerais

<div align="center">
  <table>
    <thead>
      <tr>
        <th>Modelo</th>
        <th>Métrica</th>
        <th>Dias Ensolarados</th>
        <th>Dias Nublados</th>
        <th>Geral (Teste)</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td rowspan="2" style="vertical-align: middle; text-align: center;"><b>SUNSET</b></td>
        <td align="center">RMSE</td>
        <td align="center">0.865</td>
        <td align="center">3.356</td>
        <td align="center">2.453</td>
      </tr>
      <tr>
        <td align="center">MAE</td>
        <td align="center">0.718</td>
        <td align="center">2.361</td>
        <td align="center">1.541</td>
      </tr>
      <tr>
        <td rowspan="2" style="vertical-align: middle; text-align: center;"><b>ResNet50V2</b></td>
        <td align="center">RMSE</td>
        <td align="center">0.917</td>
        <td align="center">3.786</td>
        <td align="center">2.757</td>
      </tr>
      <tr>
        <td align="center">MAE</td>
        <td align="center">0.631</td>
        <td align="center">2.642</td>
        <td align="center">1.639</td>
      </tr>
    </tbody>
  </table>
</div>

<div align="center">
  <table>
    <tr>
      <td align="center">
        <b>Resultados do modelo SUNSET</b><br>
        <img width="400" alt="Resultados do teste com o modelo SUNSET" src="https://github.com/user-attachments/assets/f6534f96-b097-4ee6-aca8-aa22ead185e5">
      </td>
      <td align="center">
        <b>Resultados do modelo ResNet50V2</b><br>
        <img width="400" alt="Resultados do teste com o modelo ResNet50V2" src="https://github.com/user-attachments/assets/91f12e67-3895-454a-8d39-62bd408f161c">
      </td>
    </tr>
  </table>
</div>


### Resumo:
- O modelo SUNSET, usado como referência, apresentou um ótimo desempenho geral (RMSE de 2.453). Fica evidente, tanto na tabela (RMSE de 0.865) quanto na imagem, sua alta precisão em dias de céu limpo. Contudo, em dias nublados, o modelo tende a "suavizar" as previsões, não conseguindo capturar as variações rápidas e bruscas da geração, o que resulta em um erro maior (RMSE de 3.356).

- A arquitetura ResNet50V2, mais complexa e adaptada com fine-tuning, mostrou um potencial significativo. Mesmo sem uma otimização aprofundada de seus hiperparâmetros, seus resultados foram muito próximos aos do baseline (RMSE de 2.757). O padrão se repete: excelente performance em dias ensolarados e maior dificuldade em dias de alta variabilidade. Isso sugere que, com uma otimização dedicada, a ResNet50V2 pode superar o modelo de referência.

De forma geral, podemos ver que ambos os modelos aprenderam bem a relação entre a geração com a posição solar nas imagens. Mesmo em dias nublados, ambos seguem bem a tendência de uma curva parabólica, típica da geração solar.

## Referências
<a id="1">[1]</a> 
Sun, Y., Szűcs, G., Brandt, A.R., 2018. Solar PV output prediction from video streams using convolutional neural networks. Energy Environ. Sci. 11, 1811–1818.

<a id="2">[2]</a> 
Nie, Y., Li, X., Scott, A., Sun, Y., Venugopal, V., & Brandt, A. (2023). SKIPP’D: A SKy Images and Photovoltaic Power Generation Dataset for short-term solar forecasting. Solar Energy, 255, 171-179.

<a id="3">[3]</a> 
Sun, Y., Venugopal, V., Brandt, A.R., 2019. Short-term solar power forecast with deep learning: Exploring optimal input and output configuration. Sol. Energy 188, 730–741.

<a id="4">[4]</a> 
Y. Nie, A. Scott, V. Venugopal, X. Li, Y. Sun, and A. Brandt, “SKIPP’D: A SKy Images and Photovoltaic Power Generation Dataset (Benchmark Data),” https://purl.stanford.edu/dj417rh1007, 2022, acessado em: 7 de julho de 2025.
