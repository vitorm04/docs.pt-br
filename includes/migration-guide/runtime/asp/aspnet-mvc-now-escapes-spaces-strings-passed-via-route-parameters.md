---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774243"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="95115-101">O MVC do ASP.NET agora escapa espaços em cadeias de caracteres passadas por meio dos parâmetros de rota</span><span class="sxs-lookup"><span data-stu-id="95115-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="95115-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="95115-102">Details</span></span>|<span data-ttu-id="95115-103">Para estar em conformidade com a RFC 2396, os espaços nos caminhos de rota agora são escapados na população dos parâmetros de ação usando uma rota.</span><span class="sxs-lookup"><span data-stu-id="95115-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="95115-104">Portanto, enquanto <code>/controller/action/some data</code> anteriormente correspondia à rota <code>/controller/action/{data}</code> e fornecia <code>some data</code> como o parâmetro de dados, ele agora fornecerá <code>some%20data</code>.</span><span class="sxs-lookup"><span data-stu-id="95115-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="95115-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="95115-105">Suggestion</span></span>|<span data-ttu-id="95115-106">O código deve ser atualizado para não escapar parâmetros de cadeia de caracteres de uma rota.</span><span class="sxs-lookup"><span data-stu-id="95115-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="95115-107">Se o URI original for necessário, ele poderá ser acessado com a API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.</span><span class="sxs-lookup"><span data-stu-id="95115-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="95115-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="95115-108">Scope</span></span>|<span data-ttu-id="95115-109">Secundário</span><span class="sxs-lookup"><span data-stu-id="95115-109">Minor</span></span>|
|<span data-ttu-id="95115-110">Versão</span><span class="sxs-lookup"><span data-stu-id="95115-110">Version</span></span>|<span data-ttu-id="95115-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="95115-111">4.5.2</span></span>|
|<span data-ttu-id="95115-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="95115-112">Type</span></span>|<span data-ttu-id="95115-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="95115-113">Runtime</span></span>|
|<span data-ttu-id="95115-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="95115-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
