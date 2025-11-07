# santander_cybersec
Conteúdo do curso santander cyber segurança 2025 

A primeira tarefa do curso foi um brute force no serviço ftp do metasploitable 2. De início, comecei verificando as portas e serviços abertos no metasploitable 2 usando o nmap com o comando 
nmap -sv -P 21,22,23,25,139,445 
que verifica se há portas com serviços não tão seguros abertos, como o ftp e telnet. 

Depois de verificar que todas elas estavam abertas, comecei o processo para conseguir a conexão com o ftp. Utilizei a ferramenta medusa para conseguir fazer brute force e descobrir o usuário e senha do ftp. Com a ferramenta medusa eu utilizei o comando: 
medusa -h 192.168.56.192 -U users.txt -P pass.txt -M ftp -t 6 

Utilizei os arquivos users.txt e pass.txt com usuários e senhas mais utilizados por padrão, e encontrei o usuário e senha, sendo msfadmin para ambos. 

No desafio da aplicação web também utilizei a ferramenta medusa para fazer brute force no formulário do dvwa. Utilizei os mesmos arquivos .txt do brute force passado, e obtive sucesso encontrando o usuário e senha da aplicação vulnerável. 

No próximo desafio que era de brute force num serviço smb, fiz a enumeração de informações para tentar achar usuários e dados sensíveis com a ferramenta enum4linux, onde encontrei alguns usuários presentes na ip alvo que poderiam ser possíveis vítimas. Depois disso criei duas wordlists, umas de usuários e uma de senhas com usuários e senhas comuns a serem utilizados, e utilizei a ferramenta medusa novamente para realizar o brute force no serviço smb. Por último fiz o teste da conexão com o smb client para avaliar o usuário e senha se estavam logando corretamente, e obtive sucesso ao tentar efetuar o login. 

Como todos estes casos foram brute force as recomendações para mitigar são as mesmas. Usar senhas fortes para todos os usuários e em vários casos, se os serviços não vão ser utilizados como o ftp ou smb, a porta deve ser fechada, mantendo apenas serviços essenciais rodando, diminuindo a possível área de ataque de um hacker. Bloqueios de ips após tentativas consecutivas também é uma estratégia interessante a ser adotada para mitigar ataques como o brute force ou password spraying, mas em muitos casos, usar uma senha forte já pode reduzir muito as chances de alguém conseguir acessar um sistema ou serviço, pois há senhas que demorariam anos para serem quebradas. Além de senhas fortes, tentar troca-las de períodos em períodos, como de 3 em 3 meses, além de adicionar verificação em duas etapas nos serviços que disponibilizarem essa opção. 
