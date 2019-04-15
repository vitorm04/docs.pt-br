---
ms.openlocfilehash: 1f06a185939c40274adad1ceac6990719069167a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235091"
---
### <a name="change-in-behavior-in-data-definition-language-ddl-apis"></a>Mudança de comportamento nas APIs DDL (Linguagem de Definição de Dados)

|   |   |
|---|---|
|Detalhes|O comportamento dos APIs DDL quando AttachDBFilename é especificado foi alterado da seguinte forma:<ul><li>As cadeias de conexão não precisam especificar um valor de Catálogo Inicial. Anteriormente, AttachDBFilename e Catálogo Inicial eram obrigatórios.</li><li>Se AttachDBFilename e Catálogo Inicial forem especificados e o arquivo MDF especificado existir, o método <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> retornará <code>true</code>. Anteriormente, o valor retornado era <code>false</code>.</li><li>Se AttachDBFilename e Catálogo Inicial forem especificados e o arquivo MDF especificado existir, chamar o método <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> excluirá o arquivo.</li><li>Se <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> for chamado quando a cadeia de conexão especificar um valor de AttachDBFilename com um MDF e um Catálogo Inicial que não existam, o método gerará uma exceção <xref:System.InvalidOperationException>. Anteriormente, ele gerava uma exceção <xref:System.Data.SqlClient.SqlException>.</li></ul>|
|Sugestão|Essas alterações facilitam a criação de ferramentas e aplicativos que usam APIs de DDL. Essas alterações podem afetar a compatibilidade do aplicativo nas seguintes situações:<ul><li>O usuário escreve um código que executará um comando <code>DROP DATABASE</code> diretamente em vez de chamar <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> se <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A> retornar <code>true</code>. Isso quebrará o código existente se o banco de dados não estiver anexado, mas um arquivo MDF existir.</li><li>O usuário escreve um código que espera o método <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A> para gerar uma <xref:System.Data.SqlClient.SqlException> em vez de uma <xref:System.InvalidOperationException> quando os arquivos de Catálogo Inicial e de MDF não existes.</li></ul>|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
