
# Instalação do Armbian na TV Box MXQ Pro 5G 4K (RK3229)

Este repositório fornece um passo a passo detalhado de como instalar o Armbian na TV Box MXQ Pro 5G 4K com chip RK3229, parte de um sistema embarcado desenvolvido no projeto de pesquisa do Instituto Federal do Rio Grande do Norte.

## Requisitos

- **Micro SD**: mínimo 8GB
- **TV Box MXQ Pro 5G 4K** com chip RK3229
- **Cabo de Rede** (Recomendado, opcional)
- **Memória NAND** na TV Box
- **Teclado e Mouse USB**
- A TV Box só é bootável a partir do cartão de memória

**Perigo**: O procedimento envolve o risco de "brickar" a TV Box e perda do sistema bootável. Proceda com cautela.

## Ferramentas

- **Multitool**: Ferramenta necessária para instalar o Armbian e descobrir o tipo de memória na TV Box. Você pode baixá-la direto desse repositorio ou [aqui](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/).

- **Balena Etcher**: Ferramenta para escrever imagens no cartão de memória. [Baixe o Balena Etcher para Windows aqui](https://www.balena.io/etcher/).

---

## Passo a Passo

### Parte 1: Preparando o Cartão de Memória

1. **Extração do Multitool**:
   - Baixe e extraia o Multitool em uma pasta no seu computador.
   
2. **Instalando o Balena Etcher**:
   - Baixe e instale o Balena Etcher.
   - Abra o Balena Etcher e clique em "Flash from file".
     ![Captura de tela 2025-02-22 174310](https://github.com/user-attachments/assets/3cf49d39-7480-49c5-a9e0-dbd5868643f1)
   - Selecione a imagem do Multitool que você extraiu.
   - Clique em "Select target" e escolha o seu **micro SD**. Tenha certeza de que o cartão de memória está correto, pois o processo apagará todos os dados.
     ![Captura de tela 2025-02-22 174330](https://github.com/user-attachments/assets/68b00a0e-f03f-4ccf-8285-83a7bbe7fded)
   - Clique em **Flash!**.
    ![Captura de tela 2025-02-22 174359](https://github.com/user-attachments/assets/02f4e486-8492-44c9-857a-98273ab8fb9b)


3. **Retire o Micro SD** do computador após a conclusão do processo.

### Parte 2: Iniciando o Multitool na TV Box

1. **Inserção do Cartão na TV Box**:
   - Com a TV Box desligada, insira o cartão de memória nela e ligue o equipamento.
   
2. **Aceitação dos Termos**:
   - Quando a tela de aceitação aparecer, leia os termos e pressione **Enter**.
     ![Captura de tela 2025-02-22 174552](https://github.com/user-attachments/assets/5dd60515-c4b1-44ab-b0a3-744697a30e1f)

3. **Detecção da Memória NAND**:
   - Uma mensagem de alerta aparecerá informando que a memória do dispositivo é do tipo **NAND**. Pressione **Enter** para continuar.
     ![Captura de tela 2025-02-22 175226](https://github.com/user-attachments/assets/854c04f6-eedd-4448-892d-1b6a925e026c)

4. **Backup do Sistema Original**:
   - O Multitool oferecerá um menu de opções. Se quiser fazer o backup do sistema original da TV Box, selecione a primeira opção utilizando as setas do teclado e pressione **Enter**.
    ![Captura de tela 2025-02-22 111118](https://github.com/user-attachments/assets/0b1e80a6-3f2f-405a-a0eb-e988a19013bd)

   - Dê um nome para o arquivo de backup e aguarde a conclusão. Após finalizar, pressione **Enter** novamente.
   - Esse processo ira demorar um pouco. Aguarde o processo finalizar.

5. **Desligamento**:
   - Após retornar ao menu principal do Multitool, selecione a opção **Shutdown** e desligue a TV Box.

6. **Cópia do Sistema Original**:
   - Retire o cartão de memória da TV Box e coloque-o de volta no computador.
   - Dentro do cartão, abra o disco chamado **MULTITOOL**. Acesse a pasta **backups** e copie o sistema operacional original para uma pasta em seu computador.

---

### Parte 3: Instalando o Armbian

1. **Download da Imagem do Armbian**:
   - Faça o download da imagem do Armbian disponível no repositório. Você pode baixá-la [aqui](https://drive.google.com/file/d/16G2Ij_zW3bQYgbVVJsmUR-PfZCeUe8Bs/view?usp=drive_link).

2. **Transferindo a Imagem para o Cartão de Memória**:
   - Dentro do disco **MULTITOOL**, acesse a pasta **images** e copie a imagem do Armbian (descompactada) para essa pasta.

3. **Instalação do Armbian**:
   - Retire o cartão de memória do PC e insira-o novamente na TV Box, com ela desligada.
   - Ligue a TV Box e aguarde inicializar.
   - No menu do Multitool, selecione **"Install Armbian via step-nand"** e pressione **Enter**. Depois, pressione **Enter** para todas as opções que aparecerem.
   - Aguarde até que o Multitool exiba a mensagem **"Scanning the source image file..."**. Isso indicará que a instalação do Armbian está em andamento.
     
     ![Captura de tela 2025-02-22 181448](https://github.com/user-attachments/assets/15a14d42-08d7-48f7-8665-ade3a714e24c)
   - Aguarde até que a instalação do Armbian seja realizada
![Captura de tela 2025-02-22 114621](https://github.com/user-attachments/assets/a9cc4ae2-f083-4c1f-bddd-6af4f00f28ad)


4. **Concluindo a Instalação**:
   - Após a instalação, o Multitool exibirá uma mensagem de sucesso. Pressione **Enter** para sair.
   - Selecione a opção **Shutdown** no menu de opçoes do multitool e desligue a TV Box.

---

### Parte 4: Primeira Inicialização do Armbian
---
#### Atenção! Nesse passo e recomendado conectar um cabo de rede ao TV Box para que tudo de certo
---
1. **Retire o Cartão e Reinicie a TV Box**:
   - Após retirar o cartão de memória, ligue novamente a TV Box.
   - Ela ficará com a tela preta por alguns segundos antes de exibir a tela de boot do Armbian.

2. **Configuração Inicial**:
   - Quando o Armbian iniciar, será exibida uma tela de configuração chamada **rk322x-box**.
     ![Captura de tela 2025-02-22 114909](https://github.com/user-attachments/assets/1daa4b84-e724-4a96-b11e-07cc9d2e1c19)
     
   - Defina a senha **root** para o sistema e pressione **Enter**.
     ![Captura de tela 2025-02-22 11490](https://github.com/user-attachments/assets/5eed2be7-6881-42b4-9e3e-1f2f0c602d82)

   - Selecione o **shell** padrão (recomenda-se o **bash**, pressionando **1**).
     ![3](https://github.com/user-attachments/assets/4020190d-52ff-4634-a166-5ef6870440e6)
     
   - Crie um nome de usuário e uma senha para ele.
     ![4](https://github.com/user-attachments/assets/f1ee605a-072b-4d60-a272-df4469811c5f)

   - O sistema detectará automaticamente sua região e perguntará se deseja usar o idioma local. Pressione **y** para confirmar.
     ![Captura de tela 2025-02-22 115004](https://github.com/user-attachments/assets/1c323050-6fb4-4e8f-a2f8-f9bb697a8c40)

   - O sistema irá realizar as configurações necessárias, aguarde até que ele esteja pronto.

3. **Finalização**:
   - Após o Armbian ser inicializado, o sistema estará quase pronto para uso.
   ![Captura de tela 2025-02-22 120019](https://github.com/user-attachments/assets/af8200f7-20eb-46d7-ab34-951190ba6d93)

---

### Parte 5: Configuração do Wi-Fi

1. **Acessando o Terminal**:
   - No Armbian, acesse o **Emulador de Terminal** (aplicações > terminal).

2. **Configurações do Sistema**:
   - No terminal, digite o comando:
     ```bash
     sudo rk322x-config
     ```
   - Pressione **Enter** e insira a senha quando solicitado.

3. **Configuração de Hardware**:
   - No menu de configurações, selecione o **chip** da sua TV Box. No caso da MXQ Pro 5G 4K, escolha **rk3229** e pressione ENTER.
     ![Captura de tela 2025-02-22 121519](https://github.com/user-attachments/assets/49681b3b-e623-4ce9-ad14-3d66eaae6bdb)

   - Selecione o tipo de memória: **nand** e pressione ENTER.
     ![Captura de tela 2025-02-22 183558](https://github.com/user-attachments/assets/dd4813bf-2978-47b4-94ab-ce16300a86a4)

   - Configure os LEDs para **R329q, MXQ-RK3229** e pressione ENTER.
      ![Captura de tela 2025-02-22 121531](https://github.com/user-attachments/assets/6077e445-f01f-46c2-911a-01f673c65cc2)
     
   - Para o módulo Wi-Fi, selecione **ssv6x5x** e pressione ENTER. Caso não funcione após reiniciar, volte nesse passo e tente a outra opção.
   - ![Captura de tela 2025-02-22 121555](https://github.com/user-attachments/assets/a0efcc87-4c68-4393-9135-40deb8eeba30)


4. **Reinício**:
   - Após concluir as configurações, no terminal, digite:
     ```bash
     sudo reboot
     ```
   - Retire o cabo de rede, se estiver usando, e aguarde o reinício.

---

## Conclusão

Pronto! Sua TV Box agora está configurada para rodar o Armbian e pode ser utilizada como um mini PC para atividades básicas, com suporte ao Wi-Fi.
---
**Recomendação**
   - Após a reinicialização recomendo que entre no terminal e digite esses comando:

     ```bash
     sudo apt update
     ```
     
     - Após isso, digite:
     ```bash
     sudo apt upgrade
     ```
   - isso ira atualizar o Armbian.

     ## REFERÊNCIAS
     
   - **Instalando Linux em TV Box com RK322X! (Armbian no MXQ e outras box similares..)**
  Canal: **VegaData**.  Você pode assistir ao vídeo [aqui](https://www.youtube.com/watch?v=R0zjwQG2iE4&t=640s).
   - **ArmBian: Uma distro Linux p/o seu TV Box RK322X**
  Canal: **RB Games Linux**. Você pode assistir ao vídeo [aqui](https://www.youtube.com/watch?v=OMuoUVIoBBo&t=1436s).
   - **CSC Armbian for RK322x TV box boards**. Você pode acessar o tópico completo no fórum [aqui](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/).



