# Relatório - Coelinhos da Páscoa

<!-- 
> [!CAUTION]
> - Lembre-se que você <ins>**não pode utilizar ferramentas de IA para
>   escrever este relatório**</ins>

## Dados do aluno

- **Cartão UFRGS**: 325091
- **Nome**: Eduardo Magnus Lazuta
-->

## Passos que eu segui para resolver o problema especificado (em formato de *"prompt"*)

<!--
> [!IMPORTANT]
> - Coloque aqui todas as informações necessárias para que alguém
>   (pessoa ou ferramenta de IA) possa reproduzir os seus passos para
>   solucionar o problema
> - Escreva em formato imperativo, como se fosse um *prompt* com as
>   instruções a serem seguidas na solução do problema
> - Seja objetivo e conciso: quanto *menos palavras* você utilizar,
>   melhor
> - Seja técnico e use terminologia adequada: assuma que quem irá ler
>   os seus passos possui conhecimento de Ciência da Computação e
>   Computação Gráfica
> - Caso você queira incluir informações "longas" (como algum *prompt*
>   grande usado com alguma ferramenta de IA), crie arquivos à parte e
>   adicione links no texto (por exemplo, crie o arquivo `PROMPTS.md`
>   e adicione um link markdown `[os prompts detalhados estão
>   aqui](PROMPTS.md)`)
> - Novamente, lembre-se que você *não pode utilizar ferramentas
>   de IA para escrever este relatório*

-->

1. Fazer os coelhos rotacionam em torno da origem:
   1. Criar 3 variáveis: num_coelhos, raio_orbita_coelho e velocidade_angular 
   2. Derivar o angulo que vai ser rotacionar coelho em torno da origem (angulo = velocidade_angular * variação de tempo)
   3. Derivar o step_posicionamento (seria a diferença em angulos de cada coelho). step_posiconamento = 2pi/num_coelhos
   4. Calcular a posição inicial do coelho vai ficar ( angulo_posicao = k-ésimo coelho * step_posicionamento);
   5. Calcula quanto o angulo final do coelho(angulo_orbita_atual = angulo_posicao - angulo)
   6. Calcular a altura variável (senoidal) do coelho:
      1. Calcula a altura do coelho utilizando uma senoidal
        -   altura_final = altura_inicial_coelho + amplitude_senoide * sin(ciclos_da_senoide * angulo_orbita_atual)
   7. Calcular se o coelho deve girar em torno dele no eixo Z, pois a cada 3 coelhos o próximo deverá girar dessa forma.
      1. Verifica se ele deve girar dessa forma: (gira_verticalmente = ((k + 1) % 4 == 0))
      2. Crie uma matriz (Mgz) que conterá o angulo (será o mesmo angulo calculado anteriormente). Caso o coelho não precise girar, apenas atribua uma matriz identidade à Mgz 
   8. Criar uma Matriz (Mcz) que vai diminuir a escala do colho passando uma constante escala_coelho;
   9.  Criar uma Matriz (Moc) que vai orientar para que o coelho fique sempre olhando para o centro;
   10. Criar uma Matriz (Mra) que vai posicionar o coelho na orbita em torno da origem e na altura calculada anteriormente;
   11. Criar uma Matriz (Maoa) que vai rotacionar o coelho para posição final do coelho;
   12. Calcula a Matriz Model do coelho (Mco) seguindo a seguinte ordem da multiplicação de matrizes;
       - Maoa Mra Moc Mcz Mgz;
   13. Desenha o coelho;
   
2. Fazer duas esferas orbitarem sobre cada coelho:
    1. Criar uma Matriz para diminuir a escala das esferas (Ms) passando uma constante escala_esfera;
    2. Criar uma Matriz para transladar as esferas (Mt) de tal forma que elas fiquem sempre uma certa constante raio_orbita do coelho;
    3. Criar uma Matriz para rotacionar (R) sobre o eixo X local do coelho, o angulo que deve ser definido da seguinte formas: angulo = velocidade_angular (definido pelo usuário) * delta tempo acumulado desde da última interação. Note que como existe uma simétria entre as esferas, deve somado pi (180 graus) ao angulo;
    4. Multiplicar da seguinte forma: Mco Mc Mr Mt Ms (Mco é a matriz model do coelho calculada anteriomente);

## Principais dificuldades encontradas durante o desenvolvimento (formato livre)
- Tive dificuldades em manter as esferas orbitando o coelho, pois elas dependiam das transformações que ocorriam com os coelhos;
- Tive dificuldades na hora de criar os coelhos e de como poderiam posicionar eles de forma que tivessem o mesmo angulo entre eles;
- Tive dificuldades na hora de atualizar a altura dos coelhos com base na função senoidal, pois nunca tinha implementado algo em algum trabalho prático (principalmente em 3 dimensões). 


## Você acha que conseguiu resolver o problema de forma adequada?
Eu acho que consegui resolver de certa forma o problema, porém como minha solução utilizou velocidade angular talvez tenha fugido um pouco da proposta do laboratório. Mas em geral, sinto que resolvi o problema da melhor forma tirando o última parte que usei a velocidade angular para ter o angulo. 

## Se você quiser compartilhar mais alguma coisa, coloque aqui:

## Se você possui alguma sugestão para o professor sobre esta atividade, coloque aqui:

