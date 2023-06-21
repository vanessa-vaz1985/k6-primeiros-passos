# Sobre o projeto
Este projeto foi desenvolvido durante o curso "Performance Test - Primeiros passos com o K6", ministrado por Alan Voigt.
O curso pode ser adquirido em https://www.udemy.com/course/performance-test-primeiros-passos-com-o-k6.
Durante este projeto, utilizei uma máquina com Windows 11, e todas as instalações/execuções foram feitas com o WSL 2, permitindo utilizar o Ubuntu 22.04 no próprio Windows.

## O que é o K6?
É uma ferramenta de teste de carga, de código aberto e gratuita, que utiliza JavaScript para criação dos cenários de teste.

## Teste de Performance
O teste de performance é o processo de avaliar o desempenho de recursos essenciais a uma infraestrutura de TI.
Velocidade, capacidade, tempo de resposta e a estabilidade de servidores, rede, softwares ou dispositivos sob uma intensa carga de trabalho são exemplos de como o teste de performance pode ajudar na avaliação da arquitetura tecnológica de uma empresa.

## Tipos de Teste de Performance
Na documentação do K6 podemos encontrar as definições dos tipos de Teste de Performance.
  https://k6.io/docs/test-types/load-test-types/

Existem vários tipos de teste. O ideal é iniciar com os testes de fumaça e posteriormente progredir para cargas mais altas e durações mais longas, de acordo com as características da aplicação a ser validada.
- Smoke tests (Teste fumaça): Valida que seu script e o sistema funcionam adequadamente com uma carga mínima.
- Average-load test (Teste de carga média): Avalia o desempenho do sistema em condições normais esperadas.
- Stress tests (Teste de stress): Avalia o comportamento do sistema quando a carga excede a média esperada.
- Soak tests (Teste de imersão): Avalia a confiabilidade e o desempenho do sistema por períodos prolongados.
- Spike tests (Teste de pico): Validam o comportamento e a sobrevivência do sistema em casos de aumentos súbitos, curtos e massivos na atividade.
- Breakpoint tests (Teste de breakpoint): Aumentam gradualmente a carga para identificar os limites de capacidade do sistema.

## Métricas
- avg: é a soma de todos os valores, dividido pela quantidade total. Ex.:
  Normal distribution
  2, 3, 3, 5, 8, 10, 11

  avg = (2 + 3 + 3 + 5 + 8 + 10 + 11)/7 = 6

- med: é o número médio entre os valores adquiridos. Ex.:
  Normal distribution
  2, 3, 3, 5, 8, 10, 11

  med = 5

- percentil (p): Supondo a seguinte situação para explicar o percentil:
  - Foi definido um requisito não funcional para aplicação, onde 90% dos usuários devem ter tempos de resposta de até 4 segundos em determinada funcionalidade.
  - Após a execução dos testes, coletamos os seguintes tempos de resposta, em segundos: 1, 4 , 4, 2, 1, 7, 8, 1, 2, 3.
  - Para aplicar o percentil, ordenamos os valores acima, ficando: 1, 1, 1, 2, 2, 3, 4, 4, 7, 8.
  - Como no nosso requisito foi definido 90%, devemos considerar o 9º valor do passo anterior, que é igual a 7.
  - Isso nos diz que 90% dos usuários levaram até 7 segundos para acessar determinada funcionalidade. Ou seja, o requisito definido não foi atendido.

## Instalando K6
- Verificar na documentação do K6 as formas de instalação: 
  https://k6.io/docs/get-started/installation/
- Neste projeto, utilizamos a instalação para Linux Ubuntu:
  
        sudo gpg -k
        sudo gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
        echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
        sudo apt-get update
        sudo apt-get install k6

## Executando testes com k6
- Para executar o k6, utilizar o comando:
  k6 run <nome-do-arquivo>.js

- Para executar um teste, definindo mais de um usuário virtual e uma duração maior, utilizar o comando (neste exemplo, um teste de carga de 30 segundos e 10 VU):
  k6 run --vus 10 --duration 30s <nome-do-arquivo>.js
