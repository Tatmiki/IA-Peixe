# FishLens

Este trabalho propõe o **uso de uma rede neural convolucional (CNN) para classificar peixes por sua espécie e então retornar imagens semelhantes de forma eficiente dentro de uma base de dados**. O objetivo é garantir uma busca a imagens semelhantes dentro de um grupo menor de imagens do dataset, que seriam aquelas com a mesma classificação da nova imagem inserida.

A ideia é que esse treinamento inicial possa ser expandido para outras bases maiores de imagens de peixe para garantir maiores taxas de acerto e melhoria relevantes ao tempo de acesso a imagens semelhantes.

## Base de dados

Esse estudo utilizou como base a coleção "*AFFiNe - Angling Freshwater Fish Netherlands*", composta por fotos mais de 7000 imagens de peixes de 30 espécies diferentes. Essa base está disponível publicamente na plataforma Kaggle.

*Link:* https://www.kaggle.com/datasets/jorritvenema/affine/data


## Metodologia

A metodologia adotada consistiu inicialmente na organização do dataset, com separação estratificada das imagens em conjuntos de treinamento, validação e teste. Em seguida, realizou-se o fine-tuning da arquitetura ResNet50 para a classificação das 468 espécies, utilizando o conjunto de validação para ajuste dos parâmetros e seleção do melhor modelo. Com a rede treinada, extraíram-se os vetores de características da penúltima camada, que foram indexados por espécie. Por fim, desenvolveu-se um sistema de busca hierárquico baseado na classificação da imagem de entrada, realizando-se a recuperação de imagens mais similares dentro das Top-3 classes preditas.
~e, quando necessário, aplicando-se uma busca global como fallback.~ (*pensando se deixo essa parte*)

#### Separação dos dados

As imagens foram divididas em 3 pastas: *train*, *validation* e *test*. Cada uma é utilizada correspondentemente no processo de treinamento (*train* e *validation*) e de testes (*test*) da rede neural. Dentro de cada uma dessas pastas existe uma subpasta para cada espécime de peixe com as imagens selecionadas para cada conjunto.

```
data/
    test/
        especie_001/
        especie_002/
        ...
        especie_468/
    train/
        especie_001/
        especie_002/
        ...
        especie_468/
    validation/
        especie_001/
        especie_002/
        ...
        especie_468/
```

Usamos a seguinte divisão de conjuntos:

- **70%** treino;
- **15%** validação;
- **15%** teste.

Obs: Essas porcentagens foram aplicadas para quantidade de imagens de cada espécime (classe).

## Métricas utilizadas



## Resultados

## Conclusão

- Uso de outra arquitetura?
  - ConvNeXt-Tiny
  - RegNetY
  - EfficientNet-B4
  - ViT-B/16

## Referências bibliográficas

> SARATH YENIGALLA; RAO, K. S.; PHALGUNI NGANGBAM. Implementation of Content-Based Image Retrieval Using Artificial Neural Networks. MDPI (MDPI AG), p. 25–25, 13 mar. 2023. 

> OWAIS, M. et al. Effective Diagnosis and Treatment through Content-Based Medical Image Retrieval (CBMIR) by Using Artificial Intelligence. Journal of Clinical Medicine, v. 8, n. 4, p. 462, 5 abr. 2019. 
