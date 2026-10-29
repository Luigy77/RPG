#Respostas às Perguntas Teóricas (Q1 a Q13)#

Q1. O arquivo chama-se rpg.db (ou similar, definido no banco.py). Ele guarda o seu banco de dados completo (todas as tabelas e as informações salvas nelas). Como é salvo em um arquivo físico no computador, os dados são persistentes: ao fechar e abrir o programa, tudo o que você cadastrou continuará lá.

Q2. As 5 tabelas são: jogadores, classes, personagens, inventario e itens. A tabela personagens tem as colunas: id, nome, nivel, jogador_id e classe_id.

Q3. Significa que o id é um número inteiro (INTEGER), é a chave primária que não se repete (PRIMARY KEY), e é gerado automaticamente e em sequência pelo banco de dados (AUTOINCREMENT). Como o próprio SQLite se encarrega de criar o próximo número sozinho, o programa não precisa (e nem deve) pedir o id no momento da inclusão.

Q4. A classe Ladino recebeu o id 5 (pois as IDs de 1 a 4 já são os dados de exemplo). Esse número é obtido no código do Python através da linha return cursor.lastrowid.

Q5. O fetchone() devolve apenas um registro (uma única linha), ideal para a busca por id, já que um ID nunca se repete. Já o fetchall() devolve uma lista com vários registros, ideal para a busca por nome, pois podem existir diversas linhas com nomes semelhantes ou que contenham o mesmo trecho.

Q6. Vão aparecer as classes que tenham "ro" no nome (como Guerreiro ou Necromante, dependendo dos dados base). Os sinais % são curingas no SQL: %ro% significa "qualquer texto, seguido de 'ro', seguido de qualquer texto".

Q7. Para evitar uma falha de segurança gravíssima chamada SQL Injection. Se concatenarmos texto com +, um usuário mal-intencionado pode digitar um comando SQL no lugar do nome e invadir ou apagar o banco de dados. Usar a tupla com o sinal ? faz o banco tratar a informação estritamente como texto, além de evitar erros se o nome digitado contiver aspas.

Q8. A inclusão ficaria apenas na memória. O conn.commit() é o que "assina" a transação e grava as alterações de verdade no arquivo. Sem ele, ao reiniciar o programa, a nova classe não estaria lá.

Q9. Sim, os resultados foram iguais. O comando LIKE no SQLite não faz distinção entre maiúsculas e minúsculas (case-insensitive) para o alfabeto básico.

Q10. O programa apresentou um erro e barrou a criação. Quem impediu foi o banco de dados (por meio de um erro de FOREIGN KEY constraint failed), pois a regra da chave estrangeira exige que um personagem só possa pertencer a um jogador_id que já exista de fato na tabela de jogadores.

Q11. Para evitar duplicação e inconsistência de dados (um processo chamado Normalização). Se o jogador mudar de apelido, basta alterar em uma única linha na tabela jogadores, e todos os seus personagens refletirão a mudança automaticamente através do JOIN.

Q12. (A resposta exata depende do que está no seu terminal, mas Gork provavelmente carrega itens de exemplo listados no banco.py, como "Poção de Vida" ou "Machado", com suas respectivas quantidades).

Q13. Uma função útil seria atualizar o nível de um personagem ou excluir um item do inventário se ele for consumido.
