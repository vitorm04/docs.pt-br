---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621012"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="10c9d-101">Permitir notação de URI relativo especial quando o Unicode estiver presente</span><span class="sxs-lookup"><span data-stu-id="10c9d-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="10c9d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="10c9d-102">Details</span></span>

<span data-ttu-id="10c9d-103"><xref:System.Uri>não gerará mais um <xref:System.NullReferenceException> ao chamar <xref:System.Uri.TryCreate%2A> em determinados URIs relativos que contenham Unicode.</span><span class="sxs-lookup"><span data-stu-id="10c9d-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="10c9d-104">A reprodução mais simples do <xref:System.NullReferenceException> está abaixo, com as duas instruções sendo equivalentes:</span><span class="sxs-lookup"><span data-stu-id="10c9d-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="10c9d-105">Para reproduzir a <xref:System.NullReferenceException>, os itens a seguir precisam ser verdadeiros:</span><span class="sxs-lookup"><span data-stu-id="10c9d-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="10c9d-106">O URI precisa ser especificado como relativo acrescentando 'http:' a ele e não inserindo '//' depois dele.</span><span class="sxs-lookup"><span data-stu-id="10c9d-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="10c9d-107">O URI precisa conter Unicode codificado por porcentagem ou símbolos não reservados.</span><span class="sxs-lookup"><span data-stu-id="10c9d-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="10c9d-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="10c9d-108">Suggestion</span></span>

<span data-ttu-id="10c9d-109">Os usuários que dependem desse comportamento para não permitir URIs relativos precisam especificar <xref:System.UriKind.Absolute?displayProperty=nameWithType> durante a criação de um URI.</span><span class="sxs-lookup"><span data-stu-id="10c9d-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="10c9d-110">Name</span><span class="sxs-lookup"><span data-stu-id="10c9d-110">Name</span></span>    | <span data-ttu-id="10c9d-111">Valor</span><span class="sxs-lookup"><span data-stu-id="10c9d-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="10c9d-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="10c9d-112">Scope</span></span>   |<span data-ttu-id="10c9d-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="10c9d-113">Edge</span></span>|
|<span data-ttu-id="10c9d-114">Versão</span><span class="sxs-lookup"><span data-stu-id="10c9d-114">Version</span></span>|<span data-ttu-id="10c9d-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="10c9d-115">4.7.2</span></span>|
|<span data-ttu-id="10c9d-116">Type</span><span class="sxs-lookup"><span data-stu-id="10c9d-116">Type</span></span>|<span data-ttu-id="10c9d-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="10c9d-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="10c9d-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="10c9d-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
