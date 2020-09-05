---
ms.openlocfilehash: c1793bb51f7da9169e912078fde202d0d62a4183
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496406"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="d498d-101">Não é mais possível definir EnableViewStateMac como false</span><span class="sxs-lookup"><span data-stu-id="d498d-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="d498d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d498d-102">Details</span></span>

<span data-ttu-id="d498d-103">O ASP.NET não permite mais que os desenvolvedores especifiquem <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="d498d-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="d498d-104">O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido.</span><span class="sxs-lookup"><span data-stu-id="d498d-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="d498d-105">Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como <code>false</code> são afetados.</span><span class="sxs-lookup"><span data-stu-id="d498d-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d498d-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="d498d-106">Suggestion</span></span>

<span data-ttu-id="d498d-107">O EnableViewStateMac deve ser considerado como true e os erros MAC resultantes devem ser resolvidos (conforme explicado nesta [diretriz](https://support.microsoft.com/kb/2915218), que contém várias resoluções dependendo das especificidades do que está causando erros de Mac).</span><span class="sxs-lookup"><span data-stu-id="d498d-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="d498d-108">Nome</span><span class="sxs-lookup"><span data-stu-id="d498d-108">Name</span></span>    | <span data-ttu-id="d498d-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d498d-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d498d-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="d498d-110">Scope</span></span>   |<span data-ttu-id="d498d-111">Principal</span><span class="sxs-lookup"><span data-stu-id="d498d-111">Major</span></span>|
|<span data-ttu-id="d498d-112">Versão</span><span class="sxs-lookup"><span data-stu-id="d498d-112">Version</span></span>|<span data-ttu-id="d498d-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="d498d-113">4.5.2</span></span>|
|<span data-ttu-id="d498d-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="d498d-114">Type</span></span>|<span data-ttu-id="d498d-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="d498d-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="d498d-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d498d-116">Affected APIs</span></span>

<span data-ttu-id="d498d-117">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="d498d-117">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
