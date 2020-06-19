# QRLJacker - QRLJacking Exploitation Framework ![Build Status](https://img.shields.io/badge/Version-2.1.1-green.svg)
### O QRLJacker é uma estrutura de exploração altamente personalizável para demonstrar "[Vetor de ataque de QRLJacking](https://www.owasp.org/index.php/Qrljacking)" para mostrar como é fácil seqüestrar serviços que dependem do QR Code como um método de autenticação e login, o objetivo principal é aumentar a conscientização de segurança sobre todos os serviços usando o QR Code como uma maneira principal de conectar usuários a diferentes serviços!

## Captura de tela
![alt img](Screenshots/Screenshot1.png)
[Tutorial do YouTube para instalar e executá-lo](https://www.youtube.com/watch?v=sYtH5-K2JZc)

## Pré-requisitos antes da instalação:
1. Linux or MacOS. (Não está funcionando no Windows)
2. Python 3.7+

## Instruções de instalação:
> Nota: Não instale o QRLJacker e o Firefox como root em uma sessão normal do usuário, pois não é suportado pelo Firefox, o que causaria erro na execução de módulos na estrutura.

***Nota importante: Se você possui várias versões python, use `python3.7` comando em vez de `python3` nas etapas a seguir e use `python3.7 -m pip` ao invés de `pip`, `pip3` ou mesmo `python3 -m pip` porque esse é o motivo de 95% dos problemas abertos aqui. Eu acho que as pessoas frequentemente pulam as partes importantes :smile:***

1. Atualize o navegador Firefox para a versão mais recente
2. Instale o último geckodriver em https://github.com/mozilla/geckodriver/releases e extraia o arquivo e faça:
	* `chmod +x geckodriver`
	* `sudo mv -f geckodriver /usr/local/share/geckodriver`
	* `sudo ln -s /usr/local/share/geckodriver /usr/local/bin/geckodriver`
	* `sudo ln -s /usr/local/share/geckodriver /usr/bin/geckodriver`
3. Clone o repositório com `git clone https://github.com/OWASP/QRLJacking` então faça `cd QRLJacking/QRLJacker`
4. Instale todos os requisitos com `pip install -r requirements.txt`
5. Agora você pode executar a estrutura com `python3 QrlJacker.py --help`

## Testado em
- Ubuntu 18.04 Bionic Beaver
- Kali Linux 2018.x para cima

## Uso
### Argumentos da linha de comando
```
uso: QrlJacker.py [-h] [-r ] [-x ] [--debug] [--dev] [--verbose] [-q]

argumentos opcionais:
  -h, --help  mostre esta mensagem de ajuda e saia.
  -r          Execute um arquivo de recurso (arquivo de histórico).
  -x          Execute um comando específico (use; para múltiplos).
  --debug     Ativa o modo de depuração (identificando problemas mais facilmente).
  --dev       Ativa o modo de desenvolvimento (recarregando módulos a cada uso).
  --verbose   Ativa o modo detalhado (Exibir mais detalhes).
  -q          Saia do modo (sem banner).
```
### Ajuda do menu principal
```
Comandos gerais
=================
	Comando               Descriação
	---------             -------------
	help/?                Mostre este menu de ajuda.
	os      <command>     Execute um comando do sistema sem fechar a estrutura.
	banner                Exibir banner.
	exit/quit             Saia da estrutura.

Comandos principais
=============
	Comando               Descrição
	---------             -------------
	database              Imprime a versão principal, verifique se a estrutura está atualizada e atualize se você não estiver atualizado.
	debug                 Entre no modo de depuração ou desative-o. (Facilitando a identificação de problemas)
	dev                   Entre no modo de desenvolvimento ou desative-o. (Recarregue os módulos a cada uso)
	verbose               Entre no modo detalhado ou desative-o. (Make framework exibe mais detalhes)
	reload/refresh        Recarregue o banco de dados dos módulos.

Comandos de recursos
==================
	Comando               Descrição
	---------             -------------
	history               Exiba o histórico mais importante da linha de comando desde o início.
	makerc                Salve os comandos mais importantes inseridos desde o início em um arquivo.
	resource  <file>      Execute os comandos armazenados em um arquivo.

Comandos de gerenciamento de sessões
============================
	Comando               Descrição
	---------             -------------
	sessions (-h)         Despejar listagens de sessão e exibir informações sobre sessões.
	jobs     (-h)         Exibe e gerencia trabalhos.

Comandos do módulo
===============
	Comando               Descrição
	---------             -------------
	list/show             Liste os módulos que você pode usar.
	use      <module>     Use um módulo disponível.
	info     <module>     Obtenha informações sobre um módulo disponível.
	previous              Executa o módulo carregado anteriormente.
	search   <text>       Procure um módulo com um texto específico em seu nome ou em sua descrição.
```
### Ajuda do menu do módulo
```
Comandos gerais
=================
	Comando               Descrição
	---------             -------------
	help/?                Mostre este menu de ajuda.
	os      <command>     Execute um comando do sistema sem fechar a estrutura.
	banner                Exibir banner.
	exit/quit             Saia da estrutura.

Comandos principais
=============
	Comando               Descrição
	---------             -------------
	database              Imprime a versão principal e, em seguida, verifique se está atualizada.
	debug                 Entre no modo de depuração ou desative-o. (Facilitando a identificação de problemas)
	dev                   Entre no modo de desenvolvimento ou desative-o. (Recarregue os módulos a cada uso)
	verbose               Entre no modo detalhado ou desative-o. (Make framework exibe mais detalhes)
	reload/refresh        Recarregue o banco de dados dos módulos.

Comandos de recursos
==================
	Comando               Descrição
	---------             -------------
	history               Exiba o histórico mais importante da linha de comando desde o início.
	makerc                Salve os comandos mais importantes inseridos desde o início em um arquivo.
	resource  <file>      Execute os comandos armazenados em um arquivo.

Comandos de gerenciamento de sessões
============================
	Comando               Descrição
	---------             -------------
	sessions (-h)         Despejar listagens de sessão e exibir informações sobre sessões.
	jobs     (-h)         Exibe e gerencia trabalhos.

Comandos do módulo
===============
	Comando               Descrição
	----------            --------------
	list/show             Liste os módulos que você pode usar.
	options               Exibe opções para o módulo atual.
	set                   Define uma variável específica do contexto para um valor.
	run                   Inicie o módulo atual.
	use     <module>      Use um módulo disponível.
	info    <module>      Obtenha informações sobre um módulo disponível.
	search  <text>        Procure um módulo com um texto específico em seu nome ou em sua descrição.
	previous              Define o módulo carregado anteriormente como o módulo atual.
	back                  Volte do contexto atual.
```
### Menu de Ajuda do Comando Sessões
```
uso: sessões [-h] [-l] [-K] [-s] [-k] [-i]

argumentos opcionais:
  -h   Mostre esta mensagem de ajuda.
  -l   Listar todas as sessões capturadas.
  -K   Remova todas as sessões capturadas.
  -s   Procure por sessões com um tipo especificado.
  -k   Remover uma sessão capturada especificada por ID.	
  -i   Interaja com uma sessão capturada por ID.
```
### Menu de ajuda do comando Jobs
```
uso: jobs [-h] [-l] [-K] [-k]

argumentos opcionais:
  -h   Mostre esta mensagem de ajuda.
  -l   Listar todos os trabalhos em execução.
  -K   Encerre todos os trabalhos em execução.
  -k   Encerrar trabalhos por ID do trabalho ou nome do módulo.
```

## Aproveitando o núcleo
### Comandos de preenchimento automático
O recurso de preenchimento automático implementado nessa estrutura não é o habitual que você sempre vê, aqui estão alguns destaques:

1. Ele foi projetado para corrigir erros de digitação nos comandos digitados no comando mais semelhante com apenas um clique na guia para `saerch` torna-se `search` e assim por diante, mesmo se você digitar qualquer palavra aleatória semelhante a um comando nesta estrutura.

2. Para vocês preguiçosos como eu, pode prever qual módulo você está tentando usar digitando qualquer parte dele. Por exemplo, se você digitou `use wh` e clique na guia, ela seria substituída por `use grabber/whatsapp` e assim por diante. Eu posso ver seu sorriso, de nada!

3. Se você digitou algum comando errado e pressionou enter, a estrutura informará qual é o comando mais próximo do que você digitou, que pode ser o que você realmente deseja.

4. Algumas coisas menos impressionantes, como o preenchimento automático para opções do módulo atual após `set` comando, preenchimento automático de módulos após `use` e `info` comandos e, finalmente, converte todas as maiúsculas para minúsculas automaticamente, caso você tenha trocado de caso por engano ao digitar.

5. Por fim, você encontrará as coisas normais de autocoplet que estava usando antes, como comandos de preenchimento automático e histórico persistente, etc...


## Automação
- Como você notou, você pode usar um arquivo de recurso a partir de argumentos da linha de comando antes de iniciar a própria estrutura ou enviar comandos diretamente.
- Dentro da estrutura, você pode usar `makerc` comando como no Metasploit, mas desta vez ele salva apenas os comandos importantes corretos.
- Tem `history` e `resource` comandos para que você não precise sair da estrutura.
- Você pode executar quantos comandos quiser ao mesmo tempo, dividindo-os com ponto-e-vírgula e muito mais para descobrir por si mesmo.
- A pesquisa de módulos no QRLJacker é tão fácil que você pode procurar um módulo pelo nome, algo escrito em sua descrição ou até mesmo pelo nome do autor.


## Relatar um problema
- Antes de relatar um problema, ative o modo de depuração usando o comando `debug` comando ou o argumento de linha de comando debug e quando o erro ocorrer novamente, a estrutura imprimirá o rastreio do erro. Além disso, o modo de depuração ativa alguns comandos ocultos que nos ajudarão na depuração do erro e na correção do problema.
- Por fim, certifique-se de que, ao relatar o problema, forneça informações muito básicas, como seu sistema, versão python e a saída do modo de depuração.

## Desenvolvimento
Se você deseja escrever seu próprio módulo, leia [os documentos de desenvolvimento a partir daqui](docs/README.md)

## Futuro ToDos:
1. Escreva módulos para outros sites e serviços.
2. Escreva módulos de pós-exploração para a estrutura.
3. TBD

## OWASP's links reference
https://www.owasp.org/index.php/QRLJacking

https://www.owasp.org/index.php/OWASP_QRLJacker
