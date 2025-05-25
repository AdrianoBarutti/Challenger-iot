# Challenger-iot

Descrição do Projeto
Este projeto é uma simulação de estacionamento para gerenciamento de vagas, desenvolvida para a empresa Moto. O sistema visa controlar a ocupação de até 100 vagas de estacionamento para motos, atribuindo automaticamente vagas livres para motos conforme uma ação de entrada.

No projeto real, a identificação e alocação da vaga são feitas por meio do escaneamento de QR Code da moto. Como não é possível simular a leitura do QR Code no ambiente atual, utilizamos um botão físico conectado ao ESP32 para substituir essa ação e disparar a simulação da alocação de vaga.

Este é o trabalho desenvolvido para o Desafio Challenger, no qual aplicamos conceitos de IoT (Internet das Coisas) e integração com plataformas de dados online para monitoramento em tempo real.

Como funciona o código
Hardware
ESP32

Botão conectado no pino GPIO 4 (com resistor interno INPUT_PULLUP), usado apenas para simulação.

Software
O ESP32 conecta-se à rede Wi-Fi Wokwi-GUEST (senha vazia).

Ao pressionar o botão (simulando o escaneamento do QR Code), o código:

Verifica se ainda existem vagas livres (máximo 100).

Escolhe aleatoriamente uma vaga livre.

Marca essa vaga como ocupada.

Gera um ID aleatório para a moto (1 a 100).

Envia os dados para o ThingSpeak via HTTP GET.

Dados enviados para o ThingSpeak
API Key: "KM1TD5SNYB924OHR" (chave para atualizar o canal ThingSpeak).

Campos enviados:

field1: ID da moto (motoID)

field2: Número da vaga (vagaID)

field3: Status da vaga (1 = ocupada)

Cada vez que o botão é pressionado, uma nova linha de dados é enviada para o canal ThingSpeak.

Visualização dos dados no ThingSpeak
Para acessar e visualizar os dados, acesse o link abaixo:
https://thingspeak.mathworks.com/channels/2971903

Lá mostra:

Gráfico 1: ID da Moto

Gráfico 2: Número da Vaga

Gráfico 3: Status da Vaga

No caso, o gráfico 3 sempre vai mostrar o número 1, pois a vaga sempre é recomendada livre e marcada como ocupada.

Como usar o código
Acesse o repositório no GitHub:
https://github.com/AdrianoBarutti/Challenger-iot.git

No repositório, abra o projeto no simulador Wokwi ou faça download do código para usar localmente.

No Wokwi, o botão já está conectado ao pino GPIO 4 e o código já está carregado.

Inicie a simulação no Wokwi.

Pressione o botão virtual para simular o escaneamento do QR Code e disparar o envio dos dados.

Observe no monitor serial a mensagem:

mathematica
Copiar
Editar
Dados enviados! Código: 200
Essa mensagem indica que os dados foram enviados com sucesso para o ThingSpeak.

Para verificar os dados em tempo real, acesse o canal ThingSpeak no link:
https://thingspeak.mathworks.com/channels/2971903
