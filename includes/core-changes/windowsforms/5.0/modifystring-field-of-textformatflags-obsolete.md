---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400624"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="ce340-101">TextFormatFlags. Modifystring é obsoleto</span><span class="sxs-lookup"><span data-stu-id="ce340-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="ce340-102">O <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> campo é obsoleto, como um aviso, e pode ser removido em uma versão futura do .net.</span><span class="sxs-lookup"><span data-stu-id="ce340-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ce340-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="ce340-103">Change description</span></span>

<span data-ttu-id="ce340-104">Nas versões anteriores do .NET, o <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> campo de enumeração não está marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="ce340-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="ce340-105">No .NET 5,0 e versões posteriores, ele é marcado como obsoleto como um aviso.</span><span class="sxs-lookup"><span data-stu-id="ce340-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="ce340-106">Esse campo pode ser removido em uma versão futura do .NET.</span><span class="sxs-lookup"><span data-stu-id="ce340-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ce340-107">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ce340-107">Reason for change</span></span>

<span data-ttu-id="ce340-108">Passar uma cadeia de caracteres para <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> com <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> altera a cadeia de caracteres em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="ce340-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="ce340-109">Esse comportamento interrompe a promessa de imutabilidade da cadeia de caracteres e pode levar a uma corrupção fatal do estado do tempo de execução .NET.</span><span class="sxs-lookup"><span data-stu-id="ce340-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce340-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ce340-110">Version introduced</span></span>

<span data-ttu-id="ce340-111">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="ce340-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce340-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ce340-112">Recommended action</span></span>

<span data-ttu-id="ce340-113">Atualize qualquer código que dependa de <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="ce340-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="ce340-114">Categoria</span><span class="sxs-lookup"><span data-stu-id="ce340-114">Category</span></span>

<span data-ttu-id="ce340-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce340-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce340-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ce340-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
