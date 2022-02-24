# Deploy com GitHub Actions.

Automatize o deploy dos seus fluxos de push ou pull requests enviados para um determiando repositório do GitHub.

Usando as actions do GitHub podemos criar um [pipeline](http://google.com/) de deploy, automatizando o envio de código para um [VPS](http://tokstok.infosec.dev.br) via SSH.

## 📜 Pré-requisitos.

Antes de começar, verifique se você atendeu aos seguintes requisitos:

- [x] Um VPS Linux [online](http://tokstok.infosec.dev.br) para o deploy. ☁️
- [x] O SSH do servidor acessível aos [endereços IP](https://api.github.com/meta) do GitHub. :octocat:
- [x] As chaves do SSH geradas. 🔑
- [x] [Secrets](https://docs.github.com/pt/actions/security-guides/encrypted-secrets) configuradas no repositório. :closed_lock_with_key:

## 💻 Gerando a chave SSH no servidor Linux.

Para que o GitHub possa se conectar no servidor e executar comandos pré e pós realizar o envio do repositório, a chave de autenticação deve ser gerada para posteriormente ser cadastrada no secret do GitHub.

Execute o seguinte comando no terminal do servidor para gerar a chave:

```bash
ssh-keygen -t rsa
```

<h4 align="center">
<details>
<summary> :arrow_heading_down: Saída esperada para a execução do comando acima.</summary>

  <p align="center">
  <br>
  <img alt="Saída de comando esperada." src="https://i.imgur.com/7ukl3Ag.png" title="Saída esperada." width="95%">
  <br>
  <sub>Saida esperada ao gerar as chaves para o SSH.</sub>
  
</p>
</details>

## 🤝 Cadastrando os secrets no repositório.

Para criar as secrets do repositório, siga estas etapas via navegado:
  
Acesse a aba `Settings` do repositório.
  
<p align="center">
<img alt="Clique na aba Settings." src="https://i.imgur.com/j4xBpMZ.png" title="Clique na aba 'Settings'." width="95%">
<br>
</p>

Agora no campo security clique em `Secrets` e depois em `Actions`, para começar a cadastrar as secrets clique em `New repository secret`.
  
<p align="center">
  <img alt="Clique em Secrets depois em Actions." src="https://i.imgur.com/LiZz0vx.png" title="Clique em 'Secrets' depois em 'Actions'." width="40%">
&nbsp; &nbsp; &nbsp; &nbsp;
  <img alt="Telegram" src="https://i.imgur.com/E7BNgZr.png" title="Clique em 'New repository secret'." width="40%">
</p>

Apenas 4 secrets são necessárias para que o deploy ocorra com com êxito, representando as seguintes informações: <kbd>porta do SSH</kbd>, <kbd>nome do usuario SSH</kbd>, <kbd>chave SSH privada</kbd> e o <kbd>endereço do servidor</kbd>.

Obedecendo o padrão de chave e valor, as secrets devem ser cadastradas com essas informações:
  
1. Crie uma chave `HOST` que deve conter o endereço do servidor (<kbd>tokstok.infosec.dev.br</kbd> nesse exemplo).  
2. Crie uma chave `KEY` que deve conter o valor da chave privada do SSH (execute para ver a sua chave <kbd>cat ~/.ssh/id_rsa</kbd>).
3. Crie uma chave `PORT` que deve conter o numero da porta do SSH (<kbd>22</kbd> nesse exemplo).
4. Crie uma chave `USERNAME` que deve conter o nome do usuário do SSH (<kbd>user</kbd> nesse exemplo).

<p align="center">
<img alt="Todos os secrets cadastrados." src="https://i.imgur.com/tylI6cn.png" title="Todos os secrets cadastrados." width="70%">
<br>
</p>

## 💚 Codar && Deployar.
  
Agora todos os envios via push ou PR (Pull Request) para o repositório vão ser entregues no servidor via SSH automaticamente. :sunglasses:

[⬆ Voltar ao topo](#deploy-com-github-actions)
