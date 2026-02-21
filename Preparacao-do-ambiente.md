
# Guia de Instalação e Configuração de Ferramentas de Desenvolvimento AWS para o treinamento da Formação AWS 5.0 do Henrylle Maia

Este guia foi desenvolvido especificamente para instalar e configurar as principais ferramentas necessárias para preparação do ambiente para realização das atividades do curso fudamentais e preparatórios da Formação AWS. 

## Visão Geral

Este documento cobre a instalação e configuração das seguintes ferramentas essenciais utilizadas na Formação AWS do Henrylle Maia:

- **AWS CLI** - Interface de linha de comando oficial da AWS para gerenciar serviços e recursos
- **AWS SAM CLI** - Ferramenta para desenvolvimento, teste e deploy de aplicações serverless
- **Node.js** - Runtime JavaScript para desenvolvimento de aplicações modernas
- **Git** - Sistema de controle de versão distribuído com configuração para GitHub
- **AWS Systems Manager (SSM)** - Plugin para gerenciamento seguro de instâncias EC2
- **Amazon Kiro CLI** - Ferramenta avançada para desenvolvimento e automação AWS

## Pré-requisitos

Antes de começar, certifique-se de que você possui:
- Sistema operacional Linux (Ubuntu/Debian ou Fedora)
- Acesso de administrador (sudo)
- Conexão com a internet
- Conta AWS ativa com credenciais de acesso

## Estrutura do Guia

Cada seção contém instruções detalhadas de instalação, verificação e configuração básica. Os comandos são apresentados de forma sequencial e incluem exemplos de saída esperada para facilitar a validação de cada etapa.

**Nota:** Todas as ferramentas listadas neste guia são fundamentais para acompanhar adequadamente o conteúdo da Formação AWS do Henrylle Maia.

---
# Instalação do aws-cli
---
Para instalar a AWS CLI, execute os comandos a seguir.
## Passo 1
Baixe o arquivo de instalação de uma das seguinte maneira:
Usar o comando curl: a opção -o especifica o nome do arquivo no qual o pacote obtido por download foi gravado. As opções no comando de exemplo a seguir gravam o arquivo obtido por download no diretório atual com o nome local awscliv2.zip.
~~~bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
~~~

## Passo 2
Descompacte o instalador. Se a distribuição do Linux não tiver um comando unzip integrado, use um equivalente para descompactá-lo. O comando de exemplo a seguir descompacta o pacote e cria um diretório chamado aws no diretório atual.
~~~bash
unzip awscliv2.zip
~~~

## Nota
Ao atualizar de uma versão anterior, o comando unzip solicita a substituição dos arquivos existentes. Para ignorar essas solicitações, como com a automação de scripts, use o sinalizador de atualização -u para unzip. Esse sinalizador atualiza automaticamente os arquivos existentes e cria outros conforme necessário.
~~~bash
unzip -u awscliv2.zip
~~~
## Passo 3
Execute o programa de instalação. O comando de instalação usa um arquivo chamado install no diretório aws recém-descompactado. Por padrão, os arquivos são todos instalados em /usr/local/aws-cli, e um link simbólico é criado em /usr/local/bin. O comando inclui sudo para conceder permissões de gravação para esses diretórios.
~~~bash
sudo ./aws/install
~~~
## Passo 4
Confirme a instalação com o comando a seguir.
~~~bash
aws --version
aws-cli/2.32.32 Python/3.13.11 Linux/5.15.167.4-microsoft-standard-WSL2 exe/x86_64.debian.13
~~~


# Instalação do aws sam
---
base 
## Passo 1: 
Baixe o arquivo AWS SAM CLI .zip para um diretório de sua escolha.
~~~ bash
wget  https://github.com/aws/aws-sam-cli/releases/latest/download/aws-sam-cli-linux-x86_64.zip
~~~ 
## Passo 2 
Descompacte os arquivos de instalação em um diretório de sua escolha. Veja a seguir um exemplo, usando o subdiretório sam-installation.
~~~ bash
unzip aws-sam-cli-linux-x86_64.zip -d sam-installation
~~~ 
## Passo 3 
Instale o AWS SAM CLI executando o install executável. Esse executável está localizado no diretório usado na etapa anterior. Veja a seguir um exemplo, usando o subdiretório sam-installation:
~~~ bash
sudo ./sam-installation/install
~~~ 
## Passo 4
Verifique a instalação.
~~~ bash
sam --version
~~~
Saida 
~~~bash
 sam --version
SAM CLI, version 1.151.0

~~~
Utilize o comando paa se conectar a sam
~~~bash  
sam init 
~~~

# Instalação do node js
--- 
 [nodejs] (https://nodejs.org/pt-br/download)
## Passo 1: 
Instalar o PPA para obter acesso aos pacotes. Do seu diretório home, utilize o curl para recuperar o script de instalação para sua versão de preferência, certificando-se de substituir o 14.x pela string da sua versão favorita (se for diferente):
~~~ bash 
cd ~
curl -sL https://deb.nodesource.com/setup_14.x -o nodesource_setup.sh
~~~

## Passo 2: 
em seguida, execute o script com o sudo:
~~~ bash
nano nodesource_setup.sh
~~~

## Passo 3: 
O PPA será adicionado à sua configuração e seu cache de pacotes local será atualizado automaticamente. Agora, você pode instalar o pacote Node.js da mesma forma que fez na seção anterior:
~~~ bash
sudo apt install nodejs
~~~ bash
## passo 4: 
- Verifique se você instalou a nova versão executando o node com o sinalizador de versão -v:
~~~ bash
node -v
npm -v 
~~~ 
O pacote nodejs do NodeSource contém tanto o binário do node quanto o npm. Por este motivo, não é necessário que você instale o npm separadamente.

# Configuração do Git
---
## Passo 1:
Configure seu nome de usuário globalmente. Este nome será usado em todos os commits:
~~~ bash
git config --global user.name "Seu Nome Completo"
~~~

## Passo 2:
Configure seu email globalmente. Use o mesmo email associado à sua conta do GitHub/GitLab:
~~~ bash
git config --global user.email "seu.email@exemplo.com"
~~~

## Passo 3:
Configure o editor padrão para o Git (opcional). Por exemplo, para usar o nano:
~~~ bash
git config --global core.editor nano
~~~
- **VS Code**
~~~ bash
git config --global core.editor "code --wait"
~~~ 

## Passo 4:
Verifique se as configurações foram aplicadas corretamente:
~~~ bash
git config --list
~~~
 - **lista apenas globais**
~~~ bash
git config --global --list 
~~~
## passo 5: 
Alterando a branch padrão para (main)
~~~ bash
git config --global init.defaultBranch main
~~~
## passo 6:
Esa configuração e mais avançada normalmente utilizado em empresas, **credential.helper** usada para especificar um programa auxiliar que lida com o armazenamento e recuperação de credenciais de autenticação, como nomes de usuário e senhas, para interagir com repositórios remotos.
~~~ bash
git config --global credential.helper <nome-do-gerenciador>
~~~
**Obs. não configurar essa opção.**
### Alguns exemplos de gerenciadores de credenciais que podem ser usados são:

- **cache**: O Git armazenará suas credenciais na memória por um período definido. Isso é útil para evitar digitar repetidamente suas credenciais durante uma sessão.
~~~ bash
git config --global credential.helper cache
~~~ 
- **store**: O Git armazenará suas credenciais em um arquivo de texto plano no sistema. Isso é útil para armazenar credenciais por mais tempo do que a opção de cache padrão.
~~~ bash
git config --global credential.helper store
~~~ 
-  **manager**: Isso permite que você use um gerenciador específico do sistema para lidar com suas credenciais. Isso pode ser útil se você estiver usando um gerenciador de senhas externo.

~~~ bash
git config --global credential.helper manager
~~~

~~~ bash

~~~

~~~ bash

~~~
## Passo 7:
Gere uma chave SSH para autenticação com repositórios remotos:
~~~ bash
ssh-keygen -t rsa -b 4096 -C "seu.email@exemplo.com"
~~~

## Passo 8:
Adicione a chave SSH ao agente SSH:
~~~ bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
~~~

## Passo 9:
Exiba a chave pública para adicionar ao seu provedor Git (GitHub/GitLab):
~~~ bash
cat ~/.ssh/id_rsa.pub
~~~

## Passo 10:
Adicione a chave SSH ao GitHub:

### 10.1: Copie a chave SSH pública
Copie todo o conteúdo exibido pelo comando anterior (começando com ssh-rsa e terminando com seu email)

### 10.2: Acesse as configurações do GitHub
- Faça login no GitHub (https://github.com)
- Clique na sua foto de perfil no canto superior direito
- Selecione "Settings" no menu dropdown

### 10.3: Navegue até SSH and GPG keys
- No menu lateral esquerdo, clique em "SSH and GPG keys"

### 10.4: Adicione uma nova chave SSH
- Clique no botão "New SSH key" (verde)
- No campo "Title", digite um nome descritivo para identificar sua máquina (ex: "Minha VM de Desenvolvimento")
- No campo "Key", cole a chave SSH pública que você copiou no passo 8.1
- Clique em "Add SSH key"

### 10.5: Confirme sua senha
- Digite sua senha do GitHub quando solicitado para confirmar a adição da chave

## Passo 11:
Teste a conexão SSH com o GitHub:
~~~ bash
ssh -T git@github.com
~~~



# Instação do SSM
---
### passo 1:
Baixe o instalador usando a seguinte URL:
~~~ bash
curl "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/ubuntu_64bit/session-manager-plugin.deb" -o "session-manager-plugin.deb"
~~~
### passo 2:
Execute o comando de instalação.
~~~ bash
sudo dpkg -i session-manager-plugin.deb
~~~
### passo 3:
Execute os comandos a seguir para verificar se a instalação do plugin do Session Manager foi bem-sucedida.
~~~ bash
session-manager-plugin
~~~
Se a instalação foi bem-sucedida, a mensagem a seguir é retornada. 
~~~ bash
The Session Manager plugin was installed successfully. Use the AWS CLI to start a session.
~~~

ou 
~~~ bash
aws ssm --version
~~~

Mosta a versão instalada do SSM 
~~~ bash
aws-cli/2.32.32 Python/3.13.11 Linux/5.15.167.4-microsoft-standard-WSL2 exe/x86_64.debian.13
~~~

## Instalação do SSM no Fedora 43

### passo 1:
Baixe o instalador RPM usando a seguinte URL:
~~~ bash
curl "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/linux_64bit/session-manager-plugin.rpm" -o "session-manager-plugin.rpm"
~~~

### passo 2:
Execute o comando de instalação usando dnf:
~~~ bash
sudo dnf install -y session-manager-plugin.rpm
~~~

Alternativamente, você pode usar rpm diretamente:
~~~ bash
sudo rpm -ivh session-manager-plugin.rpm
~~~

### passo 3:
Execute os comandos a seguir para verificar se a instalação do plugin do Session Manager foi bem-sucedida.
~~~ bash
session-manager-plugin
~~~

Se a instalação foi bem-sucedida, a mensagem a seguir é retornada:
~~~ bash
The Session Manager plugin was installed successfully. Use the AWS CLI to start a session.
~~~

ou 
~~~ bash
aws ssm --version
~~~

Mostra a versão instalada do SSM:
~~~ bash
aws-cli/2.32.32 Python/3.13.11 Linux/6.11.4-301.fc43.x86_64 exe/x86_64.fedora.43
~~~

## passo 4 (Opcional):
Caso encontre problemas de dependências, instale as dependências necessárias:
~~~ bash
sudo dnf install -y glibc
~~~
vamos utilizar os comandos abaixo para configurar a conta de acesso ao ssm no computador pessoal 

Configurando o ssm e conectando a aws 
# 1. Configure AWS CLI with your credentials
~~~ bash
aws configure
# Enter the following when prompted:
 AWS Access Key ID: [Your Access Key]
 AWS Secret Access Key: [Your Secret Key] 
 Default region name: [Your Region e.g. us-east-1]
 Default output format: table
 ~~~
# 2. Verify your AWS CLI configuration
```  aws configure list ```

# 3. Test SSM connectivity
```aws ssm get-parameter --name "test" --with-decryption```

# 4. Start a session with an EC2 instance using SSM
```aws ssm start-session --target i-xxxxxxxxxxxxxxxxx```
# 5. List all instances that can be managed by SSM
```aws ssm describe-instance-information```

# 6. Connect to instance using SSM port forwarding (for SSH)
~~~ bash
aws ssm start-session \
    --target i-xxxxxxxxxxxxxxxxx \
    --document-name AWS-StartPortForwardingSession \
    --parameters '{"portNumber":["22"],"localPortNumber":["9999"]}'
~~~ 
# 7. Test SSM plugin installation
```session-manager-plugin ```

# 8. View SSM session history
~~~ bash
aws ssm describe-sessions \
    --state History \
    --filters "key=Owner,value=$(aws sts get-caller-identity --query 'Arn' --output text)"
~~~
# 9. Terminate an active SSM session
~~~ bash
aws ssm terminate-session --session-id "session-id"
~~~

# Configurando o AWS CLI para multiplos profiles
---
O AWS CLI permite configurar múltiplos perfis (profiles) para gerenciar diferentes ambientes, contas AWS ou projetos de forma organizada e segura. Esta funcionalidade é essencial quando você trabalha com:

- **Múltiplos ambientes**: desenvolvimento, teste, homologação e produção
- **Diferentes contas AWS**: pessoal, empresarial, clientes diversos
- **Projetos distintos**: cada projeto com suas próprias credenciais e configurações
- **Diferentes regiões**: projetos que operam em regiões geográficas específicas

### Quando Usar Múltiplos Profiles

### Cenários Recomendados:
- **Separação de ambientes**: Evitar executar comandos de produção acidentalmente em desenvolvimento
- **Trabalho com múltiplos clientes**: Cada cliente possui suas próprias credenciais AWS
- **Diferentes níveis de acesso**: Perfis com permissões específicas para tarefas distintas
- **Conformidade e auditoria**: Rastreabilidade de ações por ambiente/projeto
- **Desenvolvimento em equipe**: Padronização de configurações entre desenvolvedores

### Benefícios:
- **Segurança**: Isolamento de credenciais por ambiente
- **Organização**: Configurações específicas para cada contexto
- **Produtividade**: Troca rápida entre diferentes configurações
- **Redução de erros**: Menor risco de executar comandos no ambiente errado

## Como Configurar

### Default profile
~~~ bash
aws configure
AWS Access Key ID: [Default Access Key]
AWS Secret Access Key: [Default Secret Key]
Default region name: us-east-1
Default output format: json
~~~ 
### Development profile
~~~ bash
aws configure --profile dev
AWS Access Key ID: [Dev Access Key] 
AWS Secret Access Key: [Dev Secret Key]
Default region name: us-west-2
Default output format: table
~~~
### Production profile
~~~ bash
aws configure --profile prod
AWS Access Key ID: [Prod Access Key]
AWS Secret Access Key: [Prod Secret Key] 
Default region name: eu-west-1
Default output format: text
~~~ 
### Testing profile
~~~ bash
aws configure --profile test
AWS Access Key ID: [Test Access Key]
AWS Secret Access Key: [Test Secret Key]
Default region name: ap-southeast-1 
Default output format: yaml
~~~ 
### List configured profiles
```aws configure list-profiles```

### View specific profile config
```aws configure list --profile dev```

### Use specific profile for a command
```aws s3 ls --profile prod```

### Set default profile
```export AWS_PROFILE=dev```

### Unset profile
```unset AWS_PROFILE  ```

## Instalação do Amazon Kiro CLI
---
## Instalação no Fedora

### Passo 1:
Baixe o pacote RPM do Kiro CLI:bash
```curl -L "https://github.com/aws/kiro-cli/releases/latest/download/kiro-cli-linux-x86_64.rpm" -o "kiro-cli.rpm"```
### Passo 2:
Instale o pacote usando dnf:bash
```sudo dnf install -y kiro-cli.rpm```
Alternativamente, você pode usar rpm diretamente:bash
```sudo rpm -ivh kiro-cli.rpm```
### Passo 3:
Verifique a instalação:bash
```kiro --version```
### Passo 4 (Opcional):
Caso encontre problemas de dependências, instale as dependências necessárias:bash
```sudo dnf install -y glibc openssl```
## Instalação no Ubuntu

### Passo 1:
Baixe o pacote DEB do Kiro CLI:bash
```curl -L "https://github.com/aws/kiro-cli/releases/latest/download/kiro-cli-linux-x86_64.deb" -o "kiro-cli.deb"```
### Passo 2:
Instale o pacote usando dpkg:bash
```sudo dpkg -i kiro-cli.deb```
### Passo 3:
Caso haja dependências não resolvidas, execute:bash
```sudo apt-get install -f```
### Passo 4:
Verifique a instalação:bash
```kiro --version```
## Instalação no VS Code

### Passo 1:
Abra o VS Code e acesse a aba de extensões (Ctrl+Shift+X)

### Passo 2:
Pesquise por "Amazon Kiro" na barra de busca

### Passo 3:
Clique em "Install" na extensão oficial da Amazon

### Passo 4:
Após a instalação, configure a extensão:
- Abra as configurações do VS Code (Ctrl+,)
- Pesquise por "kiro"
- Configure o caminho do executável do Kiro CLI se necessário

### Passo 5:
Verifique se a extensão está funcionando:
- Abra a paleta de comandos (Ctrl+Shift+P)
- Digite "Kiro" para ver os comandos disponíveis

### Passo 6:
Configure suas credenciais AWS no VS Code:bash
# No terminal integrado do VS Code
```aws configure```
### Passo 7:
Teste a integração criando um novo projeto Kiro:
- Use Ctrl+Shift+P
- Digite "Kiro: New Project"
- Siga as instruções na tela

