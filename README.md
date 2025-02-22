
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

- **Multitool**: Ferramenta necessária para instalar o Armbian e descobrir o tipo de memória na TV Box. Você pode baixá-la [aqui](https://forum.armbian.com/topic/34923-csc-armbian-for-rk322x-tv-box-boards/).

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

4. **Backup do Sistema Original**:
   - O Multitool oferecerá opções. Se quiser fazer o backup do sistema original da TV Box, selecione a primeira opção utilizando as setas do teclado e pressione **Enter**.
   - Dê um nome para o arquivo de backup e aguarde a conclusão. Após finalizar, pressione **Enter** novamente.

5. **Desligamento**:
   - Selecione a opção **Shutdown** e desligue a TV Box.

6. **Cópia do Sistema Original**:
   - Retire o cartão de memória da TV Box e coloque-o de volta no computador.
   - Dentro do cartão, abra o disco chamado **MULTITOOL**. Acesse a pasta **baucps** e copie o sistema operacional original para o seu computador.

---

### Parte 3: Instalando o Armbian

1. **Download da Imagem do Armbian**:
   - Faça o download da imagem do Armbian disponível no repositório.

2. **Transferindo a Imagem para o Cartão de Memória**:
   - Dentro do disco **MULTITOOL**, acesse a pasta **images** e copie a imagem do Armbian (descompactada) para essa pasta.

3. **Instalação do Armbian**:
   - Retire o cartão de memória do PC e insira-o novamente na TV Box, com ela desligada.
   - Ligue a TV Box e aguarde inicializar.
   - No menu do Multitool, selecione **"Install Armbian via step-nand"** e pressione **Enter**. Depois, pressione **Enter** para todas as opções que aparecerem.
   - Aguarde até que o Multitool exiba a mensagem **"Scanning the source image file..."**. Isso indicará que a instalação do Armbian está em andamento.

4. **Concluindo a Instalação**:
   - Após a instalação, o Multitool exibirá uma mensagem de sucesso. Pressione **Enter** para sair.
   - Selecione a opção **Shutdown** e desligue a TV Box.

---

### Parte 4: Primeira Inicialização do Armbian

1. **Retire o Cartão e Reinicie a TV Box**:
   - Após retirar o cartão de memória, ligue novamente a TV Box.
   - Ela ficará com a tela preta por alguns segundos antes de exibir a tela de boot do Armbian.

2. **Configuração Inicial**:
   - Quando o Armbian iniciar, será exibida uma tela de configuração chamada **rk322x-box**.
   - Defina a senha **root** para o sistema e pressione **Enter**.
   - Selecione o **shell** padrão (recomenda-se o **bash**, pressionando **1**).
   - Crie um nome de usuário e uma senha para ele.
   - O sistema detectará automaticamente sua região e perguntará se deseja usar o idioma local. Pressione **y** para confirmar.
   - O sistema irá realizar as configurações necessárias, aguarde até que ele esteja pronto.

3. **Finalização**:
   - Após o Armbian ser inicializado, o sistema estará pronto para uso.

---

### Parte 5: Configuração do Wi-Fi (Opcional)

1. **Acessando o Terminal**:
   - No Armbian, acesse o **Emulador de Terminal** (aplicações > terminal).

2. **Configurações do Sistema**:
   - No terminal, digite o comando:
     ```bash
     sudo rk322x-config
     ```
   - Pressione **Enter** e insira a senha quando solicitado.

3. **Configuração de Hardware**:
   - No menu de configurações, selecione o **chip** da sua TV Box. No caso da MXQ Pro 5G 4K, escolha **rk3229**.
   - Selecione o tipo de memória: **nand**.
   - Configure os LEDs para **R329q, MXQ-RK3229**.
   - Para o módulo Wi-Fi, selecione **ssv6x5x**. Caso não funcione após reiniciar, volte nesse passo e tente a outra opção.

4. **Reinício**:
   - Após concluir as configurações, no terminal, digite:
     ```bash
     sudo reboot
     ```
   - Retire o cabo de rede, se estiver usando, e aguarde o reinício.

---

## Conclusão

Pronto! Sua TV Box agora está configurada para rodar o Armbian e pode ser utilizada como um mini PC para atividades básicas, com suporte ao Wi-Fi.
