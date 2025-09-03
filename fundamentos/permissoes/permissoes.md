# Permissões no Linux

No Linux, possuimos um sistema de controle de permissão onde cada arquivo e diretório possui informações sobre: **permissões** que controlam quem pode ler, escrever ou executar.

1. Quem pode **ler** (r - read)
2. Quem pode **escrever** (w - write)
3. Quem pode **executar** (x - execute)

---

## Tipos de Usuários

Essas permissões são configuradas para três grupos distintos:

1. **Usuário (u)**: Dono do arquivo.
2. **Grupo (g)**: Grupo ao qual o arquivo pertence.
3. **Outros (o)**: Todos os demais usuários.

---

## Exibindo as  permissões

Ao executar o comando ls -l, podemos ver informações sobre permissões dos arquivos. A primeira parte do comando nos retorna a informação direta das permissões do arquivo. Cada letra, representa uma permissão habilitada do arquivo, para cada grupo.

**Exemplo de retorno:** -rw-r--r-- 1 treinamento treinamento 0 Apr 15 11:49 .htaccess

Pegamos o primeiro campo -rw-r--r-- e separamos da seguinte forma:

1. **"-":** Identificador de diretório, se for "d" é diretório/pasta
2. **"rw-":** Permissões do dono do arquivo, (rw- possui permissões para ler e escrever no arquivo, mas não para executar)
3. **"r--":** Permissões do Grupo do arquivo (r-- possui permissão apenas para ler o arquivo)
4. **"r--":** Permissões para Outros usuários (r-- possui permissão apenas para ler o arquivo)

Quando uma permissão está disponivel o caractere correspondente a ela é apresentado (rwx), quando a permissão não existe é apresentado apenas o caractere "-". 
Se um usuario que não possui acesso tenta acessar o arquivo é gerado um erro de acesso negado.
