---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065052"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="fe0f0-101">Categoria Unicode alterada para alguns caracteres latinos-1</span><span class="sxs-lookup"><span data-stu-id="fe0f0-101">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="fe0f0-102"><xref:System.Char> Agora, os métodos retornam a categoria Unicode correta para os caracteres no intervalo Latin-1.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-102"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="fe0f0-103">A categoria corresponde à do padrão Unicode.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-103">The category matches that of the Unicode standard.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fe0f0-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="fe0f0-104">Change description</span></span>

<span data-ttu-id="fe0f0-105">Nas versões anteriores do .NET, os <xref:System.Char> métodos usaram uma lista fixa de categorias Unicode para caracteres no intervalo Latin-1.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-105">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="fe0f0-106">No entanto, o padrão Unicode alterou as categorias de alguns desses caracteres desde que essas APIs foram implementadas, criando uma discrepância.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-106">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="fe0f0-107">Além disso, também havia uma discrepância entre <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> as APIs e, que seguem o padrão Unicode.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-107">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="fe0f0-108">No .NET 5,0 e versões posteriores, <xref:System.Char> os métodos usam e retornam a categoria Unicode que corresponde ao padrão Unicode para todos os caracteres.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-108">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="fe0f0-109">A tabela a seguir mostra os caracteres cujas categorias Unicode foram alteradas no .NET 5,0:</span><span class="sxs-lookup"><span data-stu-id="fe0f0-109">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="fe0f0-110">Caractere</span><span class="sxs-lookup"><span data-stu-id="fe0f0-110">Character</span></span>    | <span data-ttu-id="fe0f0-111">Categoria Unicode</span><span class="sxs-lookup"><span data-stu-id="fe0f0-111">Unicode category</span></span><br><span data-ttu-id="fe0f0-112">nas versões anteriores do .NET</span><span class="sxs-lookup"><span data-stu-id="fe0f0-112">in previous .NET versions</span></span> | <span data-ttu-id="fe0f0-113">Categoria Unicode</span><span class="sxs-lookup"><span data-stu-id="fe0f0-113">Unicode category</span></span><br><span data-ttu-id="fe0f0-114">no .NET 5,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="fe0f0-114">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="fe0f0-115">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="fe0f0-115">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="fe0f0-116">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="fe0f0-116">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="fe0f0-117">\U00ad (baixo)</span><span class="sxs-lookup"><span data-stu-id="fe0f0-117">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="fe0f0-118">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="fe0f0-118">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="fe0f0-119">º (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="fe0f0-119">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a><span data-ttu-id="fe0f0-120">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fe0f0-120">Version introduced</span></span>

<span data-ttu-id="fe0f0-121">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="fe0f0-121">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe0f0-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fe0f0-122">Recommended action</span></span>

<span data-ttu-id="fe0f0-123">Se você tiver qualquer código que obtém a categoria de caracteres Unicode usando a <xref:System.Char> classe e supõe que a categoria nunca será alterada, talvez seja necessário atualizá-la.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-123">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe0f0-124">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="fe0f0-124">Reason for change</span></span>

<span data-ttu-id="fe0f0-125">Essa alteração foi feita para que as categorias retornadas pelo <xref:System.Char> tipo sejam consistentes com o padrão Unicode e o <xref:System.Globalization.CharUnicodeInfo> tipo.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-125">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

#### <a name="category"></a><span data-ttu-id="fe0f0-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="fe0f0-126">Category</span></span>

- <span data-ttu-id="fe0f0-127">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="fe0f0-127">Core .NET libraries</span></span>
- <span data-ttu-id="fe0f0-128">Globalização</span><span class="sxs-lookup"><span data-stu-id="fe0f0-128">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe0f0-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fe0f0-129">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="fe0f0-130">Além disso, qualquer classe que depende de <xref:System.Char> obter a categoria de caractere Unicode, por exemplo, <xref:System.Text.RegularExpressions.Regex> , é afetada por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="fe0f0-130">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
