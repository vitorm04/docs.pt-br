---
ms.openlocfilehash: 39d609c955596354d1af28b4ed19d367dab0462b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619767"
---
### <a name="pageloadcomplete-event-no-longer-causes-systemwebuiwebcontrolsentitydatasource-control-to-invoke-data-binding"></a><span data-ttu-id="d1b2e-101">O evento Page.LoadComplete não faz mais com que o controle System.Web.UI.WebControls.EntityDataSource invoque a associação de dados</span><span class="sxs-lookup"><span data-stu-id="d1b2e-101">Page.LoadComplete event no longer causes System.Web.UI.WebControls.EntityDataSource control to invoke data binding</span></span>

#### <a name="details"></a><span data-ttu-id="d1b2e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="d1b2e-102">Details</span></span>

<span data-ttu-id="d1b2e-103">O evento <xref:System.Web.UI.Page.LoadComplete> não faz mais com que o controle <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> chame a associação de dados para alterações par criar/atualizar/excluir parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d1b2e-103">The <xref:System.Web.UI.Page.LoadComplete> event no longer causes the <xref:System.Web.UI.WebControls.EntityDataSource?displayProperty=fullName> control to invoke data binding for changes to create/update/delete parameters.</span></span> <span data-ttu-id="d1b2e-104">Essa alteração elimina um processamento irrelevante para o banco de dados, impede que os valores dos controles sejam redefinidos e gera um comportamento consistente com outros controles de dados, como <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> e <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d1b2e-104">This change eliminates an extraneous trip to the database, prevents the values of controls from being reset, and produces behavior that is consistent with other data controls, such as <xref:System.Web.UI.WebControls.SqlDataSource?displayProperty=fullName> and <xref:System.Web.UI.WebControls.ObjectDataSource?displayProperty=fullName>.</span></span> <span data-ttu-id="d1b2e-105">Essa alteração gera um comportamento diferente em um evento improvável no qual os aplicativos dependam da associação de dados no evento <xref:System.Web.UI.Page.LoadComplete>.</span><span class="sxs-lookup"><span data-stu-id="d1b2e-105">This change produces different behavior in the unlikely event that applications rely on invoking data binding in the <xref:System.Web.UI.Page.LoadComplete> event.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d1b2e-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="d1b2e-106">Suggestion</span></span>

<span data-ttu-id="d1b2e-107">Se houver necessidade de vinculação de dados, invoque manualmente a associação de dados em um evento que seja anterior no post-back.</span><span class="sxs-lookup"><span data-stu-id="d1b2e-107">If there is a need for databinding, manually invoke databind in an event that is earlier in the post-back.</span></span>

| <span data-ttu-id="d1b2e-108">Name</span><span class="sxs-lookup"><span data-stu-id="d1b2e-108">Name</span></span>    | <span data-ttu-id="d1b2e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d1b2e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d1b2e-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="d1b2e-110">Scope</span></span>   |<span data-ttu-id="d1b2e-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="d1b2e-111">Edge</span></span>|
|<span data-ttu-id="d1b2e-112">Versão</span><span class="sxs-lookup"><span data-stu-id="d1b2e-112">Version</span></span>|<span data-ttu-id="d1b2e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="d1b2e-113">4.5</span></span>|
|<span data-ttu-id="d1b2e-114">Type</span><span class="sxs-lookup"><span data-stu-id="d1b2e-114">Type</span></span>|<span data-ttu-id="d1b2e-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="d1b2e-115">Runtime</span></span>|
