# Script para instalar o Node.js

Para instalar e gerenciar diferentes versões do Node.js, primeiro é necessário instalar o **NVM (Node Version Manager)**.

## 1. Instalar o NVM

Abra o terminal e execute os comandos **um por vez**:

```bash
sudo apt-get update
```

```bash
sudo apt-get install build-essential libssl-dev
```

```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.7/install.sh | bash
```

## 2. Reiniciar o terminal

Feche o terminal e abra novamente para que as alterações do NVM sejam carregadas.

## 3. Verificar se o NVM foi instalado

Execute:

```bash
nvm --version
```

Se a instalação estiver correta, será exibida a versão instalada do NVM.

## 4. Listar as versões disponíveis do Node.js

Para visualizar todas as versões do Node.js disponíveis para instalação:

```bash
nvm ls-remote
```

## 5. Instalar uma versão do Node.js

Escolha a versão desejada na lista e execute o comando de instalação.

> **Observação:** no exemplo original, foi mencionada a versão `8.11.3 LTS`, mas o comando abaixo instala a versão `24.11.0`.

```bash
nvm install v24.11.0
```

## 6. Verificar a instalação

Após a instalação, verifique a versão do Node.js:

```bash
node -v
```

Se tudo estiver correto, o terminal exibirá a versão instalada do Node.js.