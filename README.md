# 👻 Israel Tech EXIF Ghost

<p align="center">
  <img src="https://img.shields.io/badge/Security-OSINT-00ff41?style=for-the-badge&logo=kali-linux&logoColor=00ff41" alt="OSINT">
  <img src="https://img.shields.io/badge/Privacy-By%20Design-008f11?style=for-the-badge" alt="Privacy by Design">
  <img src="https://img.shields.io/badge/Platform-Mobile%20%2F%20Web-black?style=for-the-badge" alt="Mobile Web">
</p>

O **Israel Tech EXIF Ghost** é uma aplicação web de página única (*Single Page Application*) projetada para auditar, analisar e sanitizar metadados ocultos em imagens (JPEG/JPG). Com uma interface inspirada em terminais de comando (*Cyberpunk/Matrix*), a ferramenta foca na soberania dos dados e na privacidade física do usuário, operando de forma 100% offline.

---

## 🚨 O Problema: O Risco Invisível dos Metadados (EXIF)

Sempre que uma fotografia é tirada por um smartphone ou câmera digital moderna, o dispositivo grava automaticamente informações ocultas no cabeçalho binário do arquivo, utilizando o padrão **EXIF (Exchangeable Image File Format)**.

### Os Riscos Práticos (Vetores de Ataque em OSINT):
* **Vazamento de Geolocalização Extrema:** Se o GPS do aparelho estiver ativo, as coordenadas exatas (Latitude e Longitude) da captura são salvas. Ao publicar essa imagem em fóruns, blogs ou plataformas que não tratam os arquivos, qualquer agente de ameaça pode mapear a rotina da vítima, encontrar seu endereço residencial ou local de trabalho.
* **Vazamento de Infraestrutura (Hardware/Software):** O EXIF expõe a marca do dispositivo, modelo, versão do sistema operacional e softwares de edição utilizados. Em engenharia social ou *penteados*, essas informações servem para identificar vulnerabilidades específicas do ecossistema do alvo.
* **Invasão de Privacidade Centralizada:** A maioria das ferramentas de análise EXIF disponíveis na internet exige que o usuário envie a imagem para um servidor de terceiros. Isso cria um novo risco: transferir dados sensíveis e fotos pessoais para servidores desconhecidos que podem registrar logs.

---

## 🛡️ A Solução: Israel Tech EXIF Ghost

A filosofia deste projeto baseia-se no **Privacy by Design** (Privacidade desde a Concepção). O EXIF Ghost resolve a ameaça de vazamento de informações e mitiga o risco de centralização de dados através de duas frentes principais:

### 1. Processamento 100% Client-Side (Offline)
A aplicação não possui *back-end* e não faz nenhuma requisição de rede para envio de arquivos. A leitura binária dos marcadores JPEG ocorre inteiramente na **memória RAM do navegador local do usuário**. Mesmo se o dispositivo estiver em Modo Avião, a extração funciona.

### 2. Sanitização Destrutiva Nativa (Remoção de Rastros)
Para apagar os metadados sem depender de softwares proprietários ou comandos complexos, a aplicação utiliza a API do **HTML5 Canvas**:
* A imagem original é renderizada em um elemento `<canvas>` em memória.
* O navegador reconstrói apenas os pixels brutos visíveis.
* O arquivo é exportado de volta como um novo binário (`Blob`) JPEG. 
* **Resultado:** Todo o cabeçalho original contendo GPS, histórico de software e dados do aparelho é destruído. A imagem nasce digitalmente estéril.

---

## ⚙️ Funcionalidades Principais

* **Dump Profundo de Tags:** Extração de metadados de hardware, lentes, software de edição e data/hora original.
* **Alerta Inteligente de GPS:** Identificação automática de coordenadas geográficas e conversão matemática de Graus/Minutos/Segundos (DMS) para formato Decimal.
* **Integração com Mapas:** Geração de link seguro e direto para o Google Maps se houver coordenadas expostas.
* **Destruidor de Metadados:** Função de download de arquivo sanitizado leve e assíncrono (evitando travamentos em dispositivos móveis).
* **Interface Responsiva:** Design flexível otimizado para navegadores Desktop e editores mobile (como Acode no Android).
* **Fundo Dinâmico Matrix:** Efeito visual imersivo renderizado via código para alto desempenho e apelo estético hacker.

---

## 🛠️ Tecnologias Utilizadas

* **HTML5 Semântico:** Estruturação para acessibilidade e leveza.
* **CSS3 Avançado:** Layout responsivo, variáveis CSS (`:root`) e efeitos de transparência (*Glassmorphism*).
* **JavaScript Puro (Vanilla JS):** Manipulação assíncrona de arquivos com `ArrayBuffer`, `Blob` e `URL.createObjectURL`.
* **Biblioteca EXIF.js:** Integração via CDN para mapeamento dos marcadores binários do arquivo de imagem.

---

## 🚀 Como Executar o Projeto

Como o projeto foi concebido para máxima portabilidade, ele está contido em um **único arquivo**.

1. Faça o download ou copie o código do arquivo `index.html`.
2. Abra o arquivo diretamente em qualquer navegador (Chrome, Firefox, Safari) no PC ou no celular.
3. Não é necessário instalar nenhuma dependência ou rodar servidores locais (como Node.js ou Apache).

---

## 📝 Licença e Autoria

Este projeto foi desenvolvido com fins educativos e de auditoria de segurança da informação.

* **Desenvolvedor:** Israel Rodrigues
* **Organização:** Israel Tech
* **Ano:** © 2026
* **Foco:** Pesquisa em Cibersegurança & Proteção de Dados

