
# 🌊 Projeto SOS Chuva – Monitoramento de Nível da Água com ESP32 e MQTT

Este projeto tem como objetivo monitorar o nível de um reservatório de água em tempo real utilizando um ESP32 com sensor ultrassônico (HC-SR04). Os dados são enviados via MQTT para um servidor e exibidos em uma página HTML responsiva, permitindo a visualização do nível atual e o estado de segurança.

## 🔧 Componentes Utilizados

- ESP32/Wokwi
- Sensor Ultrassônico HC-SR04
- Servidor MQTT (Mosquitto)
- HTML + JavaScript (MQTT via WebSockets)
- CSS

## 🚀 Funcionalidades

- Medição contínua da distância da água
- Cálculo automático do nível da água (0% a 100%)
- Envio de dados via MQTT
- Página web mostra:
  - Porcentagem do nível
  - Grafico do nivel da água
  - Estado de segurança: Seguro, Atenção ou Perigo
  - Link com orientações da Defesa Civil em caso de risco

## ⚙️ Como Usar

### 1. Configurar o Broker MQTT

- Instale o Mosquitto no servidor
- Crie o arquivo `websockets.conf` em `/etc/mosquitto/conf.d/` com o conteúdo:
  - listener 9001
  - protocol websockets
- Reinicie o Mosquitto
- Verifique se a porta 9001 está ativa com o comando `sudo ss -tulnp | grep 9001`

### 2. Código do ESP32

- Use a IDE Arduino ou Wokwi
- Instale as bibliotecas WiFi.h e PubSubClient.h
- Altere a variável `mqtt_server` com o IP do seu servidor MQTT
- Faça upload ou execute no simulador

### 3. Página Web (HTML)

- Copie os arquivos `index.html`, `style.css` e `logo.png` para a mesma pasta
- Abra o `index.html` no navegador
- O sistema se conectará automaticamente via WebSocket e exibirá os dados

## 📊 Telas do Sistema

- Exibição do nível de água em porcentagem
- Mensagem de status com cores: verde (seguro), amarelo (atenção) ou vermelho (perigo)
- Alerta com link para medidas de segurança em caso de perigo

## 🧠 Lógica de Classificação

- 0% a 60%: Seguro
- 61% a 85%: Atenção
- 86% a 100%: Perigo

## 🔗 Recursos

- Site da Defesa Civil: www.estado.rs.gov.br/saiba-o-que-fazer-em-caso-de-alagamentos-e-inundacoes
- Simulador utilizado: wokwi.com

## 📌 Observações

- A porta 9001 precisa estar aberta no firewall do servidor
- O Wi-Fi padrão do simulador Wokwi é "Wokwi-GUEST", sem senha
- Os limites de altura do reservatório podem ser ajustados no código

## 👨‍💻 Autor

Projeto desenvolvido por Matheus Caposse, Henrique Pacífico e Caio Berardo
