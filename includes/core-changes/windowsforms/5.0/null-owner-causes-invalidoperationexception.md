---
ms.openlocfilehash: b6cb7c4b479551ff4563998f310ff518d935f48a
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656323"
---
### <a name="datagridview-related-apis-now-throw-invalidoperationexception"></a><span data-ttu-id="57154-101">APIs relacionadas a DataGridView agora lança InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="57154-101">DataGridView-related APIs now throw InvalidOperationException</span></span>

<span data-ttu-id="57154-102">Algumas APIs relacionadas a <xref:System.Windows.Forms.DataGridView> agora lançam um <xref:System.InvalidOperationException> se o valor do objeto <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> for `null` .</span><span class="sxs-lookup"><span data-stu-id="57154-102">Some APIs related to <xref:System.Windows.Forms.DataGridView> now throw an <xref:System.InvalidOperationException> if the object's <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner?displayProperty=nameWithType> value is `null`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="57154-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="57154-103">Change description</span></span>

<span data-ttu-id="57154-104">Nas versões anteriores do .NET, as APIs afetadas lançam um <xref:System.NullReferenceException> quando são invocadas e o <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> valor é `null` .</span><span class="sxs-lookup"><span data-stu-id="57154-104">In previous .NET versions, the affected APIs throw a <xref:System.NullReferenceException> when they are invoked and the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null`.</span></span> <span data-ttu-id="57154-105">A partir do .NET 5,0, essas APIs lançam um <xref:System.InvalidOperationException> em vez de um <xref:System.NullReferenceException> se o <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> valor é `null` quando são invocados.</span><span class="sxs-lookup"><span data-stu-id="57154-105">Starting in .NET 5.0, these APIs throw an <xref:System.InvalidOperationException> instead of a <xref:System.NullReferenceException> if the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> value is `null` when they are invoked.</span></span>

<span data-ttu-id="57154-106">Lançar um <xref:System.InvalidOperationException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="57154-106">Throwing an <xref:System.InvalidOperationException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="57154-107">Ele também melhora a experiência de depuração com a comunicação clara da propriedade inválida.</span><span class="sxs-lookup"><span data-stu-id="57154-107">It also improves the debugging experience by clearly communicating the invalid property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="57154-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="57154-108">Version introduced</span></span>

<span data-ttu-id="57154-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="57154-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="57154-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="57154-110">Recommended action</span></span>

<span data-ttu-id="57154-111">Examine seu código e, se necessário, atualize-o para impedir a construção dos tipos afetados com a <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> propriedade como `null` .</span><span class="sxs-lookup"><span data-stu-id="57154-111">Review your code and, if necessary, update it to prevent constructing the affected types with the <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> property as `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="57154-112">Categoria</span><span class="sxs-lookup"><span data-stu-id="57154-112">Category</span></span>

<span data-ttu-id="57154-113">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="57154-113">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="57154-114">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="57154-114">Affected APIs</span></span>

<span data-ttu-id="57154-115">A tabela a seguir lista as propriedades e os parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="57154-115">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="57154-116">Propriedade ou método afetado</span><span class="sxs-lookup"><span data-stu-id="57154-116">Affected method or property</span></span> | <span data-ttu-id="57154-117">Propriedade validada</span><span class="sxs-lookup"><span data-stu-id="57154-117">Validated property</span></span> | <span data-ttu-id="57154-118">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="57154-118">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-119">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-119">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-120">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-120">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-121">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-121">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-122">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-122">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-123">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-123">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-124">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-124">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-125">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-125">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-126">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-126">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-127">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-127">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-128">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-128">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-129">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-129">5.0</span></span> |
> | <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction?displayProperty=nameWithType> | <xref:System.Windows.Forms.DataGridViewCell.DataGridViewCellAccessibleObject.Owner> | <span data-ttu-id="57154-130">5,0</span><span class="sxs-lookup"><span data-stu-id="57154-130">5.0</span></span> |

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.DataGridViewButtonCell.DataGridViewButtonCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.State`
- `M:System.Windows.Forms.DataGridViewCheckBoxCell.DataGridViewCheckBoxCellAccessibleObject.DoDefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Bounds`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DefaultAction`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Name`
- `P:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Parent`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewColumnHeaderCell.DataGridViewColumnHeaderCellAccessibleObject.Navigate(System.Windows.Forms.AccessibleNavigation)`
- `M:System.Windows.Forms.DataGridViewImageCell.DataGridViewImageCellAccessibleObject.DoDefaultAction`
- `M:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject.DoDefaultAction`

-->
