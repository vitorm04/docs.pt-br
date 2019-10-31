---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803184"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="4ae72-101">O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server</span><span class="sxs-lookup"><span data-stu-id="4ae72-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4ae72-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4ae72-102">Details</span></span>|<span data-ttu-id="4ae72-103">Quando o método <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="4ae72-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="4ae72-104">Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4ae72-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="4ae72-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4ae72-105">Suggestion</span></span>|<span data-ttu-id="4ae72-106">Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.</span><span class="sxs-lookup"><span data-stu-id="4ae72-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="4ae72-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="4ae72-107">Scope</span></span>|<span data-ttu-id="4ae72-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4ae72-108">Edge</span></span>|
|<span data-ttu-id="4ae72-109">Versão</span><span class="sxs-lookup"><span data-stu-id="4ae72-109">Version</span></span>|<span data-ttu-id="4ae72-110">4.5</span><span class="sxs-lookup"><span data-stu-id="4ae72-110">4.5</span></span>|
|<span data-ttu-id="4ae72-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="4ae72-111">Type</span></span>|<span data-ttu-id="4ae72-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="4ae72-112">Runtime</span></span>|
|<span data-ttu-id="4ae72-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4ae72-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
