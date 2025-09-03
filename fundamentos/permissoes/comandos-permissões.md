# Comandos basicos relacionados a permissões de arquivos

No linux possuimos alguns comandos relacioandos a permissão. Abaixo possuimos alguns comandos e sua explicação.

## Comandos e suas explicações:

1. **Comando chmod** 

Esse comando altera as permissões de um arquivo ou diretório.
Ele pode ser utilizado em dois modos: **numérico (octal)** e **simbólico**.

---

### Modo Numérico (Octal)

**sintaxe:** chmod <permissão> <arquivo> | Atribui a permissão numérica ao arquivo
**Exemplo:** chmod 644 teste

No formato numérico, cada permissão possui um valor:

- Leitura (r) = 4 
- Escrita (w) = 2 
- Execução (x) = 1 

Esses valores também podem ser entendidos em **binário**, onde cada permissão pode estar **ligada (1)** ou **desligada (0)**:

- rwx → 111 
- r-- → 100 
- -w- → 010 
- --x → 001 

Assim, a soma dos valores forma o número usado no `chmod`.

**Exemplos práticos:**

- `--x` → 001 (binário) = 1 = somente execução 
- `-w-` → 010 (binário) = 2 = somente escrita 
- `r--` → 100 (binário) = 4 = somente leitura 
- `rw-` → 110 (binário) = 4 + 2 = 6 = leitura + escrita 
- `rwx` → 111 (binário) = 4 + 2 + 1 = 7 = leitura + escrita + execução 

Quando aplicamos essas combinações para **usuário, grupo e outros**, obtemos números de 3 dígitos (um para cada categoria).  

**Exemplo 1:**  
- `rwx rw- rw-` → 111 110 110  
- Binário para decimal = 7 6 6  
- Permissão: `766`

**Exemplo 2:**  
- `rw- r-- ---` → 110 100 000  
- Decimal = 6 4 0  
- Permissão: `640`

---

### Modo Simbólico

**Sintaxe:** chmod <categoria><operação><permissão> <arquivo>  
- Categoria: u (usuário), g (grupo), o (outros), a (todos)  
- Operação: + (adiciona), - (remove), = (define exatamente)  
- Permissão: r (leitura), w (escrita), x (execução)  

Exemplos: 
- chmod u+x teste.sh → adiciona permissão de execução ao usuário 
- chmod g-w teste.txt → remove permissão de escrita do grupo 
- chmod o=r teste.txt → define apenas leitura para outro 
- chmod a+x script.sh → dá execução para todos 

---

2. **Comando chown**

Esse comando altera o proprietário de um arquivo ou diretório.

**Sintaxe:** chown <usuário> <arquivo> 
**Exemplo:** chown joao teste.txt

Também é possível alterar usuário e grupo ao mesmo tempo:

**Sintaxe:** chown <usuário>:<grupo> <arquivo>  
**Exemplo:** chown joao:devs teste.txt  

---

3. **Comando chgrp**

Esse comando altera apenas o grupo associado a um arquivo ou diretório.

**Sintaxe:** chgrp <grupo> <arquivo> 
**Exemplo:** chgrp devs teste.txt 

---

4. **Comando umask**

Define as permissões padrão que serão aplicadas quando novos arquivos ou diretórios forem criados.

**Sintaxe:** umask <valor> 
**Exemplo:** umask 022

Nesse caso: 
- Arquivos serão criados com permissão 644 (rw-r--r--) 
- Diretórios serão criados com permissão 755 (rwxr-xr-x)
