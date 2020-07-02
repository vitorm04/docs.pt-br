---
ms.openlocfilehash: 9c3c0bf7fbd8d45eba84eaa8634fd2d834195702
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617108"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a><span data-ttu-id="4d4ba-101">Análise de System.Uri adere à RFC 3987</span><span class="sxs-lookup"><span data-stu-id="4d4ba-101">System.Uri parsing adheres to RFC 3987</span></span>

#### <a name="details"></a><span data-ttu-id="4d4ba-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="4d4ba-102">Details</span></span>

<span data-ttu-id="4d4ba-103">A análise de URI foi alterada de várias maneiras no .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-103">URI parsing has changed in several ways in .NET Framework 4.5.</span></span> <span data-ttu-id="4d4ba-104">No entanto, observe que essas alterações afetam somente o código direcionado ao .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-104">Note, however, that these changes only affect code targeting .NET Framework 4.5.</span></span> <span data-ttu-id="4d4ba-105">Se um binário for direcionado ao .NET Framework 4.0, o comportamento antigo será observado.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-105">If a binary targets .NET Framework 4.0, the old behavior will be observed.</span></span> <span data-ttu-id="4d4ba-106">As alterações na análise de URI no .NET Framework 4.5 incluem:</span><span class="sxs-lookup"><span data-stu-id="4d4ba-106">Changes to URI parsing in .NET Framework 4.5 include:</span></span>

- <span data-ttu-id="4d4ba-107">A análise de URI executará a normalização e a verificação de caracteres de acordo com as regras mais recentes de URI na RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-107">URI parsing will perform normalization and character checking according to the latest IRI rules in RFC 3987.</span></span>
- <span data-ttu-id="4d4ba-108">O formulário C de normalização Unicode só será executado na parte de host do URI.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-108">Unicode normalization form C will only be performed on the host portion of the URI.</span></span>
- <span data-ttu-id="4d4ba-109">Agora, os URIs mailto: inválidos gerarão uma exceção.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-109">Invalid mailto: URIs will now cause an exception.</span></span>
- <span data-ttu-id="4d4ba-110">Os pontos à direita no fim de um segmento de linha agora são preservados.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-110">Trailing dots at the end of a path segment are now preserved.</span></span>
- <span data-ttu-id="4d4ba-111">Os URIs `file://` não escapam o caractere `?`.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-111">`file://` URIs do not escape the `?` character.</span></span>
- <span data-ttu-id="4d4ba-112">Os caracteres de controle Unicode `U+0080` a `U+009F` não são compatíveis.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-112">Unicode control characters `U+0080` through `U+009F` are not supported.</span></span>
- <span data-ttu-id="4d4ba-113">Os caracteres de vírgula `,` ou `%2c` não fogem ao escape automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-113">Comma characters `,` or `%2c` are not automatically unescaped.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4d4ba-114">Sugestão</span><span class="sxs-lookup"><span data-stu-id="4d4ba-114">Suggestion</span></span>

<span data-ttu-id="4d4ba-115">Se a semântica de análise de URI antiga do .NET Framework 4.0 for necessária (geralmente não é), ela poderá ser usada direcionando ao .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="4d4ba-115">If the old .NET Framework 4.0 URI parsing semantics are necessary (they often aren't), they can be used by targeting .NET Framework 4.0.</span></span> <span data-ttu-id="4d4ba-116">Isso pode ser feito usando um <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> no assembly ou pela interface do usuário do sistema do projeto no Visual Studio, na página "propriedades do projeto".</span><span class="sxs-lookup"><span data-stu-id="4d4ba-116">This can be accomplished by using a <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> on the assembly, or through Visual Studio's project system UI in the 'project properties' page.</span></span>

| <span data-ttu-id="4d4ba-117">Name</span><span class="sxs-lookup"><span data-stu-id="4d4ba-117">Name</span></span>    | <span data-ttu-id="4d4ba-118">Valor</span><span class="sxs-lookup"><span data-stu-id="4d4ba-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4d4ba-119">Escopo</span><span class="sxs-lookup"><span data-stu-id="4d4ba-119">Scope</span></span>   | <span data-ttu-id="4d4ba-120">Principal</span><span class="sxs-lookup"><span data-stu-id="4d4ba-120">Major</span></span>       |
| <span data-ttu-id="4d4ba-121">Versão</span><span class="sxs-lookup"><span data-stu-id="4d4ba-121">Version</span></span> | <span data-ttu-id="4d4ba-122">4.5</span><span class="sxs-lookup"><span data-stu-id="4d4ba-122">4.5</span></span>         |
| <span data-ttu-id="4d4ba-123">Type</span><span class="sxs-lookup"><span data-stu-id="4d4ba-123">Type</span></span>    | <span data-ttu-id="4d4ba-124">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="4d4ba-124">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4d4ba-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="4d4ba-125">Affected APIs</span></span>

- <xref:System.Uri.%23ctor(System.String)>
- <xref:System.Uri.%23ctor(System.String,System.Boolean)>
- <xref:System.Uri.%23ctor(System.String,System.UriKind)>
- <xref:System.Uri.%23ctor(System.Uri,System.String)>
- <xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType>
- <xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType>
