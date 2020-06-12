---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702424"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="e5d0d-101">As propriedades do WinForms agora geram ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="e5d0d-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="e5d0d-102">Algumas propriedades de Windows Forms agora lançam um <xref:System.ArgumentOutOfRangeException> para argumentos inválidos, onde anteriormente não.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e5d0d-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="e5d0d-103">Change description</span></span>

<span data-ttu-id="e5d0d-104">Anteriormente, essas propriedades lançavam várias exceções, como <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> ou, <xref:System.ArgumentException> quando passaram argumentos fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="e5d0d-105">A partir do .NET 5,0, essas propriedades agora lançam <xref:System.ArgumentOutOfRangeException> argumentos When passados que estão fora do intervalo.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="e5d0d-106">Lançar um <xref:System.ArgumentOutOfRangeException> está em conformidade com o comportamento do tempo de execução do .net.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="e5d0d-107">Ele também melhora a experiência de depuração ao comunicar-se claramente qual argumento é inválido.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e5d0d-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="e5d0d-108">Version introduced</span></span>

<span data-ttu-id="e5d0d-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e5d0d-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e5d0d-110">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="e5d0d-110">Recommended action</span></span>

- <span data-ttu-id="e5d0d-111">Atualize o código para evitar a passagem de argumentos inválidos.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="e5d0d-112">Se necessário, manipule um <xref:System.ArgumentOutOfRangeException> ao definir a propriedade.</span><span class="sxs-lookup"><span data-stu-id="e5d0d-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="e5d0d-113">Categoria</span><span class="sxs-lookup"><span data-stu-id="e5d0d-113">Category</span></span>

<span data-ttu-id="e5d0d-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e5d0d-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e5d0d-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e5d0d-115">Affected APIs</span></span>

<span data-ttu-id="e5d0d-116">A tabela a seguir lista as propriedades e os parâmetros afetados:</span><span class="sxs-lookup"><span data-stu-id="e5d0d-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="e5d0d-117">Propriedade</span><span class="sxs-lookup"><span data-stu-id="e5d0d-117">Property</span></span> | <span data-ttu-id="e5d0d-118">Nome do parâmetro</span><span class="sxs-lookup"><span data-stu-id="e5d0d-118">Parameter name</span></span> | <span data-ttu-id="e5d0d-119">Versão adicionada</span><span class="sxs-lookup"><span data-stu-id="e5d0d-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="e5d0d-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="e5d0d-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="e5d0d-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e5d0d-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="e5d0d-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="e5d0d-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
