---
ms.openlocfilehash: 2278d82d5362fe217ca4bce02a052d4b440843c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803188"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="1c535-101">O MVC do ASP.NET agora escapa espaços em cadeias de caracteres passadas por meio dos parâmetros de rota</span><span class="sxs-lookup"><span data-stu-id="1c535-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1c535-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1c535-102">Details</span></span>|<span data-ttu-id="1c535-103">Para estar em conformidade com a RFC 2396, os espaços nos caminhos de rota agora são escapados na população dos parâmetros de ação usando uma rota.</span><span class="sxs-lookup"><span data-stu-id="1c535-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="1c535-104">Portanto, enquanto <code>/controller/action/some data</code> anteriormente correspondia à rota <code>/controller/action/{data}</code> e fornecia <code>some data</code> como o parâmetro de dados, ele agora fornecerá <code>some%20data</code>.</span><span class="sxs-lookup"><span data-stu-id="1c535-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>|
|<span data-ttu-id="1c535-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1c535-105">Suggestion</span></span>|<span data-ttu-id="1c535-106">O código deve ser atualizado para não escapar parâmetros de cadeia de caracteres de uma rota.</span><span class="sxs-lookup"><span data-stu-id="1c535-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="1c535-107">Se o URI original for necessário, ele poderá ser acessado com a API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.</span><span class="sxs-lookup"><span data-stu-id="1c535-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>|
|<span data-ttu-id="1c535-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="1c535-108">Scope</span></span>|<span data-ttu-id="1c535-109">Secundária</span><span class="sxs-lookup"><span data-stu-id="1c535-109">Minor</span></span>|
|<span data-ttu-id="1c535-110">Versão</span><span class="sxs-lookup"><span data-stu-id="1c535-110">Version</span></span>|<span data-ttu-id="1c535-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="1c535-111">4.5.2</span></span>|
|<span data-ttu-id="1c535-112">Type</span><span class="sxs-lookup"><span data-stu-id="1c535-112">Type</span></span>|<span data-ttu-id="1c535-113">Runtime</span><span class="sxs-lookup"><span data-stu-id="1c535-113">Runtime</span></span>|
|<span data-ttu-id="1c535-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1c535-114">Affected APIs</span></span>|<ul><li><xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)?displayProperty=nameWithType></li></ul>|
