---
ms.openlocfilehash: e77e37156de759856c8a6f2e0c009caf9e1fe826
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497091"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="baec7-101">O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server</span><span class="sxs-lookup"><span data-stu-id="baec7-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="baec7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="baec7-102">Details</span></span>

<span data-ttu-id="baec7-103">Quando o método <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="baec7-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="baec7-104">Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="baec7-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="baec7-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="baec7-105">Suggestion</span></span>

<span data-ttu-id="baec7-106">Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.</span><span class="sxs-lookup"><span data-stu-id="baec7-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="baec7-107">Nome</span><span class="sxs-lookup"><span data-stu-id="baec7-107">Name</span></span>    | <span data-ttu-id="baec7-108">Valor</span><span class="sxs-lookup"><span data-stu-id="baec7-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="baec7-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="baec7-109">Scope</span></span>   |<span data-ttu-id="baec7-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="baec7-110">Edge</span></span>|
|<span data-ttu-id="baec7-111">Versão</span><span class="sxs-lookup"><span data-stu-id="baec7-111">Version</span></span>|<span data-ttu-id="baec7-112">4.5</span><span class="sxs-lookup"><span data-stu-id="baec7-112">4.5</span></span>|
|<span data-ttu-id="baec7-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="baec7-113">Type</span></span>|<span data-ttu-id="baec7-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="baec7-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="baec7-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="baec7-115">Affected APIs</span></span>

- <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.Objects.ObjectContext.CreateDatabase`

-->
