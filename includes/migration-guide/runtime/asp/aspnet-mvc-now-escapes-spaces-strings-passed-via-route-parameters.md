---
ms.openlocfilehash: afbf34710c75d0f0586ddfdb2e7937d8d76d5399
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496431"
---
### <a name="aspnet-mvc-now-escapes-spaces-in-strings-passed-in-via-route-parameters"></a><span data-ttu-id="697c0-101">O MVC do ASP.NET agora escapa espaços em cadeias de caracteres passadas por meio dos parâmetros de rota</span><span class="sxs-lookup"><span data-stu-id="697c0-101">ASP.NET MVC now escapes spaces in strings passed in via route parameters</span></span>

#### <a name="details"></a><span data-ttu-id="697c0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="697c0-102">Details</span></span>

<span data-ttu-id="697c0-103">Para estar em conformidade com a RFC 2396, os espaços nos caminhos de rota agora são escapados na população dos parâmetros de ação usando uma rota.</span><span class="sxs-lookup"><span data-stu-id="697c0-103">In order to conform to RFC 2396, spaces in route paths are now escaped when populating action parameters from a route.</span></span> <span data-ttu-id="697c0-104">Portanto, enquanto <code>/controller/action/some data</code> anteriormente correspondia à rota <code>/controller/action/{data}</code> e fornecia <code>some data</code> como o parâmetro de dados, ele agora fornecerá <code>some%20data</code>.</span><span class="sxs-lookup"><span data-stu-id="697c0-104">So, whereas  <code>/controller/action/some data</code> would previously match the route <code>/controller/action/{data}</code> and provide <code>some data</code> as the data parameter, it will now provide <code>some%20data</code> instead.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="697c0-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="697c0-105">Suggestion</span></span>

<span data-ttu-id="697c0-106">O código deve ser atualizado para não escapar parâmetros de cadeia de caracteres de uma rota.</span><span class="sxs-lookup"><span data-stu-id="697c0-106">Code should be updated to unescape string parameters from a route.</span></span> <span data-ttu-id="697c0-107">Se o URI original for necessário, ele poderá ser acessado com a API <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString.</span><span class="sxs-lookup"><span data-stu-id="697c0-107">If the original URI is needed, it can be accessed with the <xref:System.Net.HttpWebRequest.RequestUri>.OriginalString API.</span></span>

| <span data-ttu-id="697c0-108">Nome</span><span class="sxs-lookup"><span data-stu-id="697c0-108">Name</span></span>    | <span data-ttu-id="697c0-109">Valor</span><span class="sxs-lookup"><span data-stu-id="697c0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="697c0-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="697c0-110">Scope</span></span>   |<span data-ttu-id="697c0-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="697c0-111">Minor</span></span>|
|<span data-ttu-id="697c0-112">Versão</span><span class="sxs-lookup"><span data-stu-id="697c0-112">Version</span></span>|<span data-ttu-id="697c0-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="697c0-113">4.5.2</span></span>|
|<span data-ttu-id="697c0-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="697c0-114">Type</span></span>|<span data-ttu-id="697c0-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="697c0-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="697c0-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="697c0-116">Affected APIs</span></span>

- <xref:System.Web.Mvc.RouteAttribute.%23ctor(System.String)>

<!--

#### Affected APIs

- `M:System.Web.Mvc.RouteAttribute.#ctor(System.String)`

-->
