Alura - Pacman com PyGame 1 - Cenário e Ator
===============================

[ ] TODO - Preencher
----------

```python
# Surface é um tipo de objeto que representa uma imagem na biblioteca Pygame.

# Cria uma tela gráfica com o módulo display  e método set_mode
tela = pygame.display.set_mode((width, height), flags, depth)

# Parametros. Surface, Tupla que representa uma cor RGB, Tupla com coordenadas  x e y, raio, espessura do traço
pygame.draw.circle(tela, (255, 255, 255), (320, 240), 50, 5)

pygame.draw.circle(<objeto Surface>, (tupla cor), (tupla ponto central), <raio>, <espessura>)

pygame.display.update() # evita efeito flick, primeiro tudo é pintado numa area de memória e depois é transferido para o monitor.

<objeto surface>.set_at((tupla posição), (tupla cor)) # desenha um pixel

pygame.draw.rect(<objeto Surface>, (tupla cor), (tupla ponto superior esquerdo, <largura>, <altura>), <esspessura>)

pygame.Rect((tupla ponto superior esquerdo), <largura>, <altura>)

pygame.draw.polygon(<objeto Surface>, (tupla cor), (tupla pontos), <espessura>)

# Frames por segundo
# Pode se utilizar o módulo time da biblioteca para forçar uma quantidade de frames por segundo. Um loop de jogo sem estratégia de FPS é executado conformete disponbilidade de processamento. FPS normaliza a execução do jogo.

pygame.time.delay(<milissegundos>)

# Ou usar a classe Clock
# Inicialização
clock = pygame.time.Clock()

# Dentro do loop do jogo
clock.tick(<quantidade de frames por segundo>) # O método tick consegue balancear o método delay dependendo da quantidade de processamento diferente a cada volta do laço, garantindo o FPS estipulado.

# Persistência de visão, sensação de movimento contínuo identificada pelo cerébro em padrões de pelo menos 16 FPS 

# Tipos de eventos

QUIT # Ocorre ao se clicar no botão de fechar da tela. Sem propriedades.
ACTIVEEVENT # Tela do pygame foi ativada ou escondida. Propriedades: gain, state.
KEYDOWN # Uma ou mais teclas foram pressionadas. Propriedades: unicode, key, mod.
KEYUP # Uma ou mais teclas foram soltas. Propriedades: key, mod.
MOUSEMOTION # Mouse foi movido. Propriedades: pos, rel, buttons.
MOUSEBUTTONDOWN # Um ou mais botões do mouse foram pressionados. Propriedades: pos, button.
MOUSEBUTTONUP # Um ou mais botões do mouse foram soltos. Propriedades: pos, button.
VIDEORESIZE # Tela do pygame teve o tamanho alterado. Propriedades: size, w, h.
USEREVENT # Ocorreu algum evento de usuário. Propriedades: code.

# Fila de eventos
# O módulo event guarda uma fila com todos os eventos que ocorreram no último instante. Esta fila pode ser acessada do método get(). Quando o método get() é executado a fila é esvaziada.
        for e in pygame.event.get():
            if e.type == pygame.QUIT:
                exit()

# O tabuleiro também pode ser feito utilizando um recurso do Python
# para criação de matrizes descomente o codigo abaixo para testar
# matriz = [[(c+l) % 2 == 0 for c in range(8)] for l in range(8)]

# Primeiro deve-se criar o objeto do tipo Font, ou SysFont, depois fazer o render() do texto e por último fazer o blit().

# Módulo font do pygame possui duas classes: Font e SysFont. 
# Essas classes permitem converter textos em Surfaces que podem ser coladas em outras Surfaces por meio da função blit()

# A classe SysFont gera objetos do tipo Font baseado em uma fonte do sistema.
<obj Font> = pygame.font.SysFont(<nome da fonte>, <tamanho>, <bold>, <italic>)

font = pygame.font.SysFont("arial", 48, True, False)

# A classe Font permite utilizar fontes TrueType

<obj Font> = pygame.font.Font(<caminho da fonte>, <tamanho>) # Não tem parametros para bold e italic, pois espera-se que cada fonte TrueType tenha essa alternativas em arquivos separados.

font = pygame.font.Font("c:/Windows/Fonts/arial.ttf", 48)

# Após serem carregadas, o objeto criado pode renderisar textos tranformando-os em imagens.

<obj Surface> = <obj Font>.render(<texto>, <antialias>, (tupla cor do texto), (tupla cor do fundo)) # antialias é um algoritmo que evita efeito serrilhado, se true evita ficando mais lisa.
    # Se a cor de fundo náo for passada, o default é transparente.

# Por último a surface gerada é colada em outra com o comando blit()

# Inicialização do módulo de fontes
# pygame.font.init() ou pygame.init(), este último inicia vários módulos

# Abstrair consiste em ignorar elementos irrelevantes e focar nos que são mais importantes. 

# As máquinas de estados finitos são máquinas abstratas, que capturam as partes essenciais de algumas máquinas concretas

# Alternativa correta! As máquinas de estados finitos são assim chamadas porque representam uma quantidade finita de estados, e são também abstratas porque representam apenas os estados mais relevantes do sistema.

Para que o efeito de Persistência de Visão ocorra, é preciso mostrar diversas imagens, com pequenas alterações, a uma velocidade de alguns quadros por segundo. Dessa forma, a retina do olho percebe a animação como um movimento contínuo.

Alternativa correta! Com apenas 16 quadros por segundo, é possível manter a percepção de um movimento contínuo. Algumas documentações referem-se a 24 quadros por segundo, mas 16 já são suficientes. Os jogos rodam a pelo menos 30 quadros por segundo, para garantir esse efeito.


'''
