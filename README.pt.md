# Detector de gestos através de visão computacional

<img src="https://i.imgur.com/x8p2Ygk.jpg" width="250" height="250">

*Read this in other languages: [English](https://github.com/jaaoop/ProjectGestus), [Portuguese](https://github.com/jaaoop/ProjectGestus/tree/master/Lang/README.pt.md).*

## Funcionamento do projeto

### Descrição

O seguinte projeto tem como foco detectar gestos da mão com a webcam e atribuir funcionalidades para as detecções, como mover personagem em um vídeo-game ou controlar peças de hardware.

## Recomendações ao usuário para utilizar o repositório
- Utilize o conda para criar ambientes virtuais.
- Use cuda e cudnn para ter um melhor desempenho (verifique se a GPU é compatível).
- Recomenda-se Linux para realizar os procedimentos.

## Instalação

### Python 

Recomenda-se versão 3.7.

### Crie um ambiente virtual com o conda

`conda create -n <nome-do-ambiente> python=3.7`<br/>
`conda activate <nome-do-ambiente>` 

### Dependências necessárias

**Instalação em uma linha**<br/>
`pip install tensorflow-gpu==1.15.2 opencv-python opencv-contrib-python numpy scipy matplotlib`

- ### TensorFlow (recomenda-se versões <= 1.15.2)
`pip install tensorflow==1.15.2` (CPU)<br/>
`pip install tensorflow-gpu==1.15.2` (GPU)

- ### OpenCV
`pip install opencv-python opencv-contrib-python`

- ### Numpy
`pip install numpy`

- ### SciPy
`pip install scipy`

- ### MatPlotLib
`pip install matplotlib`

### Baixe o repositório
Faça download do repositório ou clone executando no terminal `git clone https://github.com/jaaoop/ProjectGestus.git`. Após esses passos estará pronto para uso.

### Arquivos com passo a passo

[**ContinuousGesturePredictor.py**](https://github.com/jaaoop/ProjectGestus/blob/master/ContinuousGesturePredictor.py) faz a detecção em tempo real dos gestos. 
1. Execute no terminal `python ContinuousGesturePredictor.py` .
2. Ao abrir o arquivo a webcam iniciará e a filmagem será mostrada ao usuário.
3. Na janela aberta um quadrado será desenhado e, durante 30 frames, pegará a área do desenho como *background*. Portanto, deixe essa área livre da mão para melhores resultados.
4. Após os 30 frames iniciais, a janela *Thresholded and Statistics* irá aparecer, nesse momento o usuário deve apertar a tecla '**s**' para começar a detecção e, então, posicionar a mão no quadrado desenhado.
5. A janela *Thresholded and Statistics* aparecerá com o nome do gesto detectado, o usuário é livre para fazer movimentos e testar novas detecções.

[**LabelGenerator.py**](https://github.com/jaaoop/ProjectGestus/blob/master/LabelGenerator.py) gera novos gestos para treino.
1. Execute no terminal `python LabelGenerator.py -n <nome-do-gesto>`.
2. Ao abrir o arquivo a webcam iniciará e a filmagem será mostrada ao usuário.
3. Na janela aberta um quadrado será desenhado e, durante 30 frames, pegará a área do desenho como *background*. Portanto, deixe essa área livre da mão para melhores resultados.
4. Após os 30 frames iniciais, a janela *Thresholded* irá aparecer, nesse momento o usuário deve posicionar a mão no quadrado desenhado e apertar a tecla '**s**' para começar a gerar os gestos de treino e teste. **Sugestão:** Mova a mão para diversificar os resultados.
5. No processo de criação do novo gesto, o console irá mostrar o progresso. Ao finalizar, duas pastas serão criadas, uma de [Treino](https://github.com/jaaoop/ProjectGestus/tree/master/Dataset/Train) e uma de [Teste](https://github.com/jaaoop/ProjectGestus/tree/master/Dataset/Test), ambas com o nome do gesto.

>**Nota:** Um parâmetro adicional do LabelGenerator é `-t <numero-de-imagens>` onde define-se a quantia de imagens para treino, já as de teste são 10% desse valor. Por padrão o parâmetro é `-t 1000`.

[**ModelTrainer.py**](https://github.com/jaaoop/ProjectGestus/blob/master/ModelTrainer.py) treina o modelo para detectar novos gestos.
1. Certifique-se que possui as mesmas pastas em [Treino](https://github.com/jaaoop/ProjectGestus/tree/master/Dataset/Train) e [Teste](https://github.com/jaaoop/ProjectGestus/tree/master/Dataset/Test).
2. Execute no terminal `python ModelTrainer.py`.
3. Aguarde até o final do treinamento.

>**Nota:** Um parâmetro adicional do ModelTrainer é `-c True` que permite salvar o gráfico de treino. Por padrão o parâmetro é `-c False`.

### Implementações do código

Os seguintes arquivos vão se comportar da mesma maneira que `ContinousGesturePredictor.py`, com a exceção que para cada gesto uma ação é designada, como mover personagem de vídeo game ou pressionar uma tecla do teclado. O arquivo `basicApplication.py` é a estrutura de código das implementações sem as atribuições, o usuário é capaz de configurar as ações de acordo com suas necessidades.

[**basicApplication.py**](https://github.com/jaaoop/ProjectGestus/blob/master/basicApplication.py) template para possíveis aplicações .
1. Execute no terminal `python basicApplication.py` .
2. O arquivo vai ser comportar da mesma maneira que `ContinousGesturePredictor.py` se o usuário não atribuir nenhuma ação.

[**runwNotes.py**](https://github.com/jaaoop/ProjectGestus/blob/master/runwNotes.py) demo de aplicação usando um editor de texto.
1. Execute no terminal `python runwNotes.py` .
2. Se o editor de texto estiver aberto, o usuário deve ver na tela os caracteres designados de acordo com os gestos.

>**Note:** Outras dependências podem ser necessárias para algumas aplicações.

[**runwMinecraft.py**](https://github.com/jaaoop/ProjectGestus/blob/master/runwMinecraft.py) demo para controlar movimentos no Minecraft.
1. Execute no terminal `python runwMinecraft.py` .
2. Se a janela do minecraft estiver aberta, o personagem deve ser mover de acordo com a detecção.

>**Note:** Outras dependências podem ser necessárias para algumas aplicações.

[**runwArduino.py**](https://github.com/jaaoop/ProjectGestus/blob/master/runwArduino.py) demo para Arduino.
1. Execute no terminal `python runwArduino.py` .
2. Se um Arduino estiver conectado, o usuário deve ver comandos sendo passados de acordo com a detecção.

>**Note:** Outras dependências podem ser necessárias para algumas aplicações.

## Informações
Este projeto é parte dos projetos da RAS Unesp Bauru. Para mais informações a respeito desse e outros projetos, acesse: https://sites.google.com/unesp.br/rasunespbauru/home.

## Autores

- [**Artur Starling**](https://github.com/ArturStarling)
- [**Fabrício Amoroso**](https://github.com/FabricioAmoroso)
- [**Gustavo Stahl**](https://github.com/GustavoStah)
- [**João Gouvêa**](https://github.com/jaaoop)

## Licença

Este projeto é gratuito e sem fins lucrativos.

## Creditos

O projeto foi baseado no repositório [Hand Gesture Recognition using Convolution Neural Network built using Tensorflow, OpenCV and python](https://github.com/SparshaSaha/Hand-Gesture-Recognition-Using-Background-Elllimination-and-Convolution-Neural-Network).
