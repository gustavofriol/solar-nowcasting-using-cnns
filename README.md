# Estimativa da geração instantânea (nowcasting) de painéis solares a partir de imagens do céu

 O presente repositório foi criado para documentar os resultados do projeto final da disciplina de Aprendizado de Máquina do Professor Danilo Silva da Universidade Federal de Santa Catarina.
 O trabalho foi feito por mim, Gustavo, com auxílio do professor Danilo durante o semestre de 2025/1.

## Introdução

A volatilidade das condições meteorológicas faz com que a previsão a curto prazo da geração solar seja extremamente desafiadora. Mudanças repentinas na cobertura de nuvens podem ocasionar variações significativas na geração solar numa escala de minutos, o que se torna um empecilho na insercção dessa fonte nas redes de energia ao redor do mundo. Em condições parcialmente nubladas, por exemplo, a potência gerada por painéis fotovoltaicos pode praticamente zerar em menos de um minuto.

Em [1], Sun et al. comprovam que imagens do céu capturadas localmente podem fornecer informações relevantes na previsão da geração de um sistema fotovoltaico. Dentro da imagem, a posição do sol se correlaciona diretamente com a insolação teórica. A distribuição, a cor e a transparência das nuvens afetam a absorção e a reflexão da luz. O movimento e a forma das nuvens até mesmo prenunciam futuras imagens do céu e, consequentemente, a futura produção de energia fotovoltaica. Tais informações são difíceis de extrair com modelos explícitos, o que tem motivado um grupo recente de pesquisadores a empregar técnicas de machine learning para capturar essas relações, visando a uma previsão a curto prazo mais confiável.
