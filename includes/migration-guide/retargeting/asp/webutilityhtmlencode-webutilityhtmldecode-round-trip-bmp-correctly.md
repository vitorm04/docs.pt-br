---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617102"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a><span data-ttu-id="3553c-101">WebUtility.HtmlEncode e WebUtility.HtmlDecode vão e voltam corretamente ao BMP</span><span class="sxs-lookup"><span data-stu-id="3553c-101">WebUtility.HtmlEncode and WebUtility.HtmlDecode round-trip BMP correctly</span></span>

#### <a name="details"></a><span data-ttu-id="3553c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="3553c-102">Details</span></span>

<span data-ttu-id="3553c-103">Nos aplicativos destinados ao .NET Framework 4.5, os caracteres fora do BMP (Basic Multilingual Plane) vão e voltam corretamente quando são passados para os métodos <xref:System.Net.WebUtility.HtmlDecode(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="3553c-103">For applications that target the .NET Framework 4.5, characters that are outside the Basic Multilingual Plane (BMP) round-trip correctly when they are passed to the <xref:System.Net.WebUtility.HtmlDecode(System.String)> methods.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3553c-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="3553c-104">Suggestion</span></span>

<span data-ttu-id="3553c-105">Essa alteração não deve ter efeito sobre os aplicativos atuais, mas para restaurar o comportamento original, defina o `targetFramework` atributo do `<httpRuntime>` elemento como uma cadeia de caracteres diferente de "4,5".</span><span class="sxs-lookup"><span data-stu-id="3553c-105">This change should have no effect on current applications, but to restore the original behavior, set the `targetFramework` attribute of the `<httpRuntime>` element to a string other than "4.5".</span></span> <span data-ttu-id="3553c-106">Você também pode definir os atributos `unicodeEncodingConformance` e `unicodeDecodingConformance` do elemento de configuração `<webUtility>` para controlar esse comportamento independentemente da versão de destino do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3553c-106">You can also set the `unicodeEncodingConformance` and `unicodeDecodingConformance` attributes of the `<webUtility>` configuration element to control this behavior independently of the targeted version of the .NET Framework.</span></span>

| <span data-ttu-id="3553c-107">Name</span><span class="sxs-lookup"><span data-stu-id="3553c-107">Name</span></span>    | <span data-ttu-id="3553c-108">Valor</span><span class="sxs-lookup"><span data-stu-id="3553c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3553c-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="3553c-109">Scope</span></span>   | <span data-ttu-id="3553c-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="3553c-110">Edge</span></span>        |
| <span data-ttu-id="3553c-111">Versão</span><span class="sxs-lookup"><span data-stu-id="3553c-111">Version</span></span> | <span data-ttu-id="3553c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="3553c-112">4.5</span></span>         |
| <span data-ttu-id="3553c-113">Type</span><span class="sxs-lookup"><span data-stu-id="3553c-113">Type</span></span>    | <span data-ttu-id="3553c-114">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="3553c-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="3553c-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="3553c-115">Affected APIs</span></span>

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
