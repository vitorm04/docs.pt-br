---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235113"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="f193a-101">O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server</span><span class="sxs-lookup"><span data-stu-id="f193a-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f193a-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f193a-102">Details</span></span>|<span data-ttu-id="f193a-103">Quando o método <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="f193a-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="f193a-104">Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f193a-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="f193a-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="f193a-105">Suggestion</span></span>|<span data-ttu-id="f193a-106">Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.</span><span class="sxs-lookup"><span data-stu-id="f193a-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="f193a-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="f193a-107">Scope</span></span>|<span data-ttu-id="f193a-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="f193a-108">Edge</span></span>|
|<span data-ttu-id="f193a-109">Versão</span><span class="sxs-lookup"><span data-stu-id="f193a-109">Version</span></span>|<span data-ttu-id="f193a-110">4.5</span><span class="sxs-lookup"><span data-stu-id="f193a-110">4.5</span></span>|
|<span data-ttu-id="f193a-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="f193a-111">Type</span></span>|<span data-ttu-id="f193a-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="f193a-112">Runtime</span></span>|
|<span data-ttu-id="f193a-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f193a-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
