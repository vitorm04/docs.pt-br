---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619797"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="10674-101">O nome do arquivo de log criado pelo método ObjectContext.CreateDatabase foi alterado para corresponder às especificações do SQL Server</span><span class="sxs-lookup"><span data-stu-id="10674-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="10674-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="10674-102">Details</span></span>

<span data-ttu-id="10674-103">Quando o método <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> é chamado diretamente ou usando Code First com o provedor SqlClient e um valor AttachDBFilename na cadeia de conexão, ele cria um arquivo de log chamado filename_log.ldf em vez de filename.ldf (onde filename é o nome do arquivo especificado pelo valor AttachDBFilename).</span><span class="sxs-lookup"><span data-stu-id="10674-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="10674-104">Essa alteração melhora a depuração ao fornecer um arquivo de log chamado de acordo com especificações do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="10674-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="10674-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="10674-105">Suggestion</span></span>

<span data-ttu-id="10674-106">Se o nome do arquivo de log for importante para um aplicativo, o aplicativo deverá ser atualizado para esperar o formato de nome de arquivo _log.ldf padrão.</span><span class="sxs-lookup"><span data-stu-id="10674-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="10674-107">Name</span><span class="sxs-lookup"><span data-stu-id="10674-107">Name</span></span>    | <span data-ttu-id="10674-108">Valor</span><span class="sxs-lookup"><span data-stu-id="10674-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="10674-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="10674-109">Scope</span></span>   |<span data-ttu-id="10674-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="10674-110">Edge</span></span>|
|<span data-ttu-id="10674-111">Versão</span><span class="sxs-lookup"><span data-stu-id="10674-111">Version</span></span>|<span data-ttu-id="10674-112">4.5</span><span class="sxs-lookup"><span data-stu-id="10674-112">4.5</span></span>|
|<span data-ttu-id="10674-113">Type</span><span class="sxs-lookup"><span data-stu-id="10674-113">Type</span></span>|<span data-ttu-id="10674-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="10674-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10674-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="10674-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
