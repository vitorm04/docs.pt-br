---
ms.openlocfilehash: 3e4a5936bbac4e77efc5f7e68b55ddf49bae5d43
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614283"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="72f45-101">Verificações de dois-pontos em caminhos estão mais rigorosas</span><span class="sxs-lookup"><span data-stu-id="72f45-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="72f45-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="72f45-102">Details</span></span>

<span data-ttu-id="72f45-103">No .NET Framework 4.6.2, uma série de alterações foram feitas para dar suporte aos caminhos incompatíveis anteriormente (em termos de comprimento e formato).</span><span class="sxs-lookup"><span data-stu-id="72f45-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="72f45-104">As verificações de sintaxe do separador de unidades (dois-pontos) correto foram aperfeiçoadas, o que teve como efeito colateral o bloqueio de alguns caminhos de URI em algumas APIs de Caminho selecionadas em que eles costumavam ser aceitos.</span><span class="sxs-lookup"><span data-stu-id="72f45-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they used to be tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="72f45-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="72f45-105">Suggestion</span></span>

<span data-ttu-id="72f45-106">Ao passar um URI para as APIs afetadas, modifique a cadeia de caracteres para um caminho correto antes.</span><span class="sxs-lookup"><span data-stu-id="72f45-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span><ul><li><span data-ttu-id="72f45-107">Remova o esquema das URLs manualmente (por exemplo, remova `file://` das URLs).</span><span class="sxs-lookup"><span data-stu-id="72f45-107">Remove the scheme from URLs manually (e.g. remove `file://` from URLs)</span></span>

- <span data-ttu-id="72f45-108">Passe o URI para a classe <xref:System.Uri> e use <xref:System.Uri.LocalPath>.</span><span class="sxs-lookup"><span data-stu-id="72f45-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath></span></span>

<span data-ttu-id="72f45-109">Como alternativa, é possível recusar a normalização do novo caminho definindo a opção AppContext `Switch.System.IO.UseLegacyPathHandling` como true.</span><span class="sxs-lookup"><span data-stu-id="72f45-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to true.</span></span>

| <span data-ttu-id="72f45-110">Name</span><span class="sxs-lookup"><span data-stu-id="72f45-110">Name</span></span>    | <span data-ttu-id="72f45-111">Valor</span><span class="sxs-lookup"><span data-stu-id="72f45-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="72f45-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="72f45-112">Scope</span></span>   | <span data-ttu-id="72f45-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="72f45-113">Edge</span></span>        |
| <span data-ttu-id="72f45-114">Versão</span><span class="sxs-lookup"><span data-stu-id="72f45-114">Version</span></span> | <span data-ttu-id="72f45-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="72f45-115">4.6.2</span></span>       |
| <span data-ttu-id="72f45-116">Type</span><span class="sxs-lookup"><span data-stu-id="72f45-116">Type</span></span>    | <span data-ttu-id="72f45-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="72f45-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="72f45-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="72f45-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
