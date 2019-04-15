---
ms.openlocfilehash: dbe96abebdc61fae469f7727673e6fcb93cbc739
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236616"
---
### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a><span data-ttu-id="5d9e8-101">Não é mais possível definir EnableViewStateMac como false</span><span class="sxs-lookup"><span data-stu-id="5d9e8-101">No longer able to set EnableViewStateMac to false</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5d9e8-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5d9e8-102">Details</span></span>|<span data-ttu-id="5d9e8-103">O ASP.NET não permite mais que os desenvolvedores especifiquem <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> ou <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span><span class="sxs-lookup"><span data-stu-id="5d9e8-103">ASP.NET no longer allows developers to specify <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> or <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>.</span></span> <span data-ttu-id="5d9e8-104">O MAC (Message Authentication Code) de estado da exibição agora é obrigatório em todas as solicitações com estado de exibição embutido.</span><span class="sxs-lookup"><span data-stu-id="5d9e8-104">The view state message authentication code (MAC) is now enforced for all requests with embedded view state.</span></span> <span data-ttu-id="5d9e8-105">Apenas aplicativos que definiram explicitamente a propriedade EnableViewStateMac como <code>false</code> são afetados.</span><span class="sxs-lookup"><span data-stu-id="5d9e8-105">Only apps that explicitly set the EnableViewStateMac property to <code>false</code> are affected.</span></span>|
|<span data-ttu-id="5d9e8-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5d9e8-106">Suggestion</span></span>|<span data-ttu-id="5d9e8-107">EnableViewStateMac deve ser considerada true e qualquer erro MAC resultante deverá ser resolvido (conforme explicado [nestas diretrizes](https://support.microsoft.com/kb/2915218), que contêm várias resoluções que variam de acordo com as características do que está causando os erros MAC).</span><span class="sxs-lookup"><span data-stu-id="5d9e8-107">EnableViewStateMac must be assumed to be true, and any resulting MAC errors must be resolved (as explained in [this guidance](https://support.microsoft.com/kb/2915218), which contains multiple resolutions depending on the specifics of what is causing MAC errors).</span></span>|
|<span data-ttu-id="5d9e8-108">Escopo</span><span class="sxs-lookup"><span data-stu-id="5d9e8-108">Scope</span></span>|<span data-ttu-id="5d9e8-109">Principal</span><span class="sxs-lookup"><span data-stu-id="5d9e8-109">Major</span></span>|
|<span data-ttu-id="5d9e8-110">Versão</span><span class="sxs-lookup"><span data-stu-id="5d9e8-110">Version</span></span>|<span data-ttu-id="5d9e8-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="5d9e8-111">4.5.2</span></span>|
|<span data-ttu-id="5d9e8-112">Tipo</span><span class="sxs-lookup"><span data-stu-id="5d9e8-112">Type</span></span>|<span data-ttu-id="5d9e8-113">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5d9e8-113">Runtime</span></span>|
