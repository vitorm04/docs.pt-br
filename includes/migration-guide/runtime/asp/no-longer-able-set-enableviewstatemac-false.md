---
ms.openlocfilehash: cecb7b2abd4f57fdaacb0ea373cc19dc3cd9b24a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619769"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="b3611-101">Não é mais possível definir EnableViewStateMac como false</span><span class="sxs-lookup"><span data-stu-id="b3611-101">No longer able to set EnableViewStateMac to false</span></span>

#### <a name="details"></a><span data-ttu-id="b3611-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b3611-102">Details</span></span>

<span data-ttu-id="b3611-103">O ASP.NET não permite mais que os desenvolvedores especifiquem <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="b3611-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="b3611-104">O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido.</span><span class="sxs-lookup"><span data-stu-id="b3611-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="b3611-105">Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como <code>false</code> são afetados.</span><span class="sxs-lookup"><span data-stu-id="b3611-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b3611-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b3611-106">Suggestion</span></span>

<span data-ttu-id="b3611-107">O EnableViewStateMac deve ser considerado como true e os erros MAC resultantes devem ser resolvidos (conforme explicado nesta [diretriz](https://support.microsoft.com/kb/2915218), que contém várias resoluções dependendo das especificidades do que está causando erros de Mac).</span><span class="sxs-lookup"><span data-stu-id="b3611-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>

| <span data-ttu-id="b3611-108">Name</span><span class="sxs-lookup"><span data-stu-id="b3611-108">Name</span></span>    | <span data-ttu-id="b3611-109">Valor</span><span class="sxs-lookup"><span data-stu-id="b3611-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b3611-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="b3611-110">Scope</span></span>   |<span data-ttu-id="b3611-111">Principal</span><span class="sxs-lookup"><span data-stu-id="b3611-111">Major</span></span>|
|<span data-ttu-id="b3611-112">Versão</span><span class="sxs-lookup"><span data-stu-id="b3611-112">Version</span></span>|<span data-ttu-id="b3611-113">4.5.2</span><span class="sxs-lookup"><span data-stu-id="b3611-113">4.5.2</span></span>|
|<span data-ttu-id="b3611-114">Type</span><span class="sxs-lookup"><span data-stu-id="b3611-114">Type</span></span>|<span data-ttu-id="b3611-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="b3611-115">Runtime</span></span>|
