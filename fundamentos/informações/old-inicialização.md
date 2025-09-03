Ao se iniciar o linux, são usados diversos scripts presentes no diretório /etc para configurar o sistema e mudar e um nivel de execução de outro, esse processo varia um pouco entre as distribuições

Processo init

Iniit = inicialização do controle de processos. É o pai de todos os processos, criado a partir de um script armazenado em /etc/inittab.
PID:1


Runlevels - niveis de execução

O conceito de n´´iveis de execução especifica as diferentes formas pelas quais um sistema pode ser utilizado e o controle sobre quais serviços rodarão.
Os niveis de execução são especificados pelos numeros inteiros de 0 a 6.
O processo init é respondavel por levar o sistema de execução padrão.

uma configuração que especifica o que vai rodar e o que não vai rodar naquele momento no computador

0 = Sistema desligado
1, S, s - Modo Monousuário
2 - Multiusuário; padrão no Debian.
3 - Multiusuário. Padrão no Red Hat, sem GUI.
4 - Não usado
5 - Multiusuário completo com login gráfico (Red Hat)
6 - Reinicialização de sistema.


/etc/init.d

Diretório que contém scripts de inicialização/encerramento para cada serviço do sistema.
Exemplo: /etc/init.d/sshd

Esses scripts aceitam argumentos como start, stop, restart, status e reload.

Esses scripts não são executados diretamente pelo processo init. em vez disso, os diretórios /etc/rc0.d a /etc/rc6.d possuem links simbólicos para esses scripts.


/etc/rc0.d a /etc/rc6.d

Os links são nomeados nos formatos KNNnome e SNNnome

K = Kill ("finalizar"): Servições que não deverão rodar nesse run level, executados primeiro.
S = Start ("iniciar"): Serviços que deverão rodar no runlevel.
NN = Número de sequência (Ordem de execução dos scripts).
Nome = identifcação dos scripts



O padrão utilizado pode ser visto no arquivo /etc/inittab, com o comando head /etc/inittab.


Você consegue alterar o runlevel em tempo de execução
telinit [numero]
