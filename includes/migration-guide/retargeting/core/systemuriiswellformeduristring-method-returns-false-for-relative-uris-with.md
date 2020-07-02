---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617109"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a><span data-ttu-id="6c1a5-101">Método System.Uri.IsWellFormedUriString retorna false para URIs com dois-pontos no primeiro segmento</span><span class="sxs-lookup"><span data-stu-id="6c1a5-101">System.Uri.IsWellFormedUriString method returns false for relative URIs with a colon char in first segment</span></span>

#### <a name="details"></a><span data-ttu-id="6c1a5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6c1a5-102">Details</span></span>

<span data-ttu-id="6c1a5-103">A partir do .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> tratará URIs relativos com um `:` no primeiro segmento como malformados.</span><span class="sxs-lookup"><span data-stu-id="6c1a5-103">Beginning with the .NET Framework 4.5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> will treat relative URIs with a `:` in their first segment as not well formed.</span></span> <span data-ttu-id="6c1a5-104">Essa é uma alteração do comportamento de <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> no .NET Framework 4.0, realizada para manter a conformidade com a RFC3986.</span><span class="sxs-lookup"><span data-stu-id="6c1a5-104">This is a change from <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> behavior in the .NET Framework 4.0 that was made to conform to RFC3986.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6c1a5-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="6c1a5-105">Suggestion</span></span>

<span data-ttu-id="6c1a5-106">Essa alteração (assim como várias outras alterações de URI) afetará somente os aplicativos do .NET Framework 4.5 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="6c1a5-106">This change (like many other URI changes) will only affect applications targeting the .NET Framework 4.5 (or later).</span></span> <span data-ttu-id="6c1a5-107">Para continuar usando o comportamento antigo, direcione o aplicativo para o .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="6c1a5-107">To keep using the old behavior, target the app against the .NET Framework 4.0.</span></span> <span data-ttu-id="6c1a5-108">Como alternativa, verifique se há caracteres `:` no URI que você deseja remover para fins de validação antes de chamar <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> se quiser usar o comportamento antigo.</span><span class="sxs-lookup"><span data-stu-id="6c1a5-108">Alternatively, scan URI's prior to calling <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> looking for `:` characters that you may want to remove for validation purposes, if the old behavior is desirable.</span></span>

| <span data-ttu-id="6c1a5-109">Name</span><span class="sxs-lookup"><span data-stu-id="6c1a5-109">Name</span></span>    | <span data-ttu-id="6c1a5-110">Valor</span><span class="sxs-lookup"><span data-stu-id="6c1a5-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6c1a5-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="6c1a5-111">Scope</span></span>   | <span data-ttu-id="6c1a5-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="6c1a5-112">Minor</span></span>       |
| <span data-ttu-id="6c1a5-113">Versão</span><span class="sxs-lookup"><span data-stu-id="6c1a5-113">Version</span></span> | <span data-ttu-id="6c1a5-114">4.5</span><span class="sxs-lookup"><span data-stu-id="6c1a5-114">4.5</span></span>         |
| <span data-ttu-id="6c1a5-115">Type</span><span class="sxs-lookup"><span data-stu-id="6c1a5-115">Type</span></span>    | <span data-ttu-id="6c1a5-116">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="6c1a5-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="6c1a5-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="6c1a5-117">Affected APIs</span></span>

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
