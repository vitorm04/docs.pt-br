### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Mudança de comportamento nas APIs DDL (Linguagem de Definição de Dados)

|   |   |
|---|---|
|Detalhes|O comportamento dos APIs DDL quando AttachDBFilename é especificado foi alterado da seguinte forma:<ul><li>As cadeias de conexão não precisam especificar um valor de Catálogo Inicial. Anteriormente, AttachDBFilename e Catálogo Inicial eram obrigatórios.</li><li>Se AttachDBFilename e Catálogo Inicial forem especificados e o arquivo MDF fornecido existir, o método ObjectContext.DatabaseExists retornará true. Antigamente, ele retornava false.</li><li>Se AttachDBFilename e Catálogo Inicial forem especificados e o arquivo MDF fornecido existir, chamar o método ObjectContext.DeleteDatabase excluirá os arquivos.</li><li>Se ObjectContext.DeleteDatabase for chamado quando a cadeia de conexão especificar um valor AttachDBFilename com um MDF e um Catálogo Inicial que não existem, o método vai gerar uma exceção InvalidOperationException. Antigamente, ele gerava uma exceção SqlException.</li></ul>|
|Sugestão|Essas alterações facilitam a criação de ferramentas e aplicativos que usam APIs de DDL. Essas alterações podem afetar a compatibilidade do aplicativo nas seguintes situações:<ul><li>O usuário escreve um código que executa um comando DROP DATABASE diretamente, em vez de chamar ObjectContext.DeleteDatabase se ObjectContext.DatabaseExists retornar true. Isso quebrará o código existente se o banco de dados não estiver anexado, mas um arquivo MDF existir.</li><li>O usuário escreve um código que espera que o método ObjectContext.DeleteDatabase gere uma exceção SqlException, em vez de uma exceção InvalidOperationException quando o Catálogo Inicial e o arquivo MDF não existirem.</li></ul>|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|

