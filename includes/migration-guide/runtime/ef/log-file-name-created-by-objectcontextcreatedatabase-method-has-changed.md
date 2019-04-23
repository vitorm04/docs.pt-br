---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803184"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server

|   |   |
|---|---|
|Detalhes|Quando o método <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename). Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.|
|Sugestão|Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
