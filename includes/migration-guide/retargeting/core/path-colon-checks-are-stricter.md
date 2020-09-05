---
ms.openlocfilehash: 6af63c0a58a3273aa98fa70f22e3637b481806b4
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497187"
---
### <a name="path-colon-checks-are-stricter"></a><span data-ttu-id="0b690-101">Verificações de dois-pontos em caminhos estão mais rigorosas</span><span class="sxs-lookup"><span data-stu-id="0b690-101">Path colon checks are stricter</span></span>

#### <a name="details"></a><span data-ttu-id="0b690-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0b690-102">Details</span></span>

<span data-ttu-id="0b690-103">No .NET Framework 4.6.2, uma série de alterações foram feitas para dar suporte aos caminhos incompatíveis anteriormente (em termos de comprimento e formato).</span><span class="sxs-lookup"><span data-stu-id="0b690-103">In .NET Framework 4.6.2, a number of changes were made to support previously unsupported paths (both in length and format).</span></span> <span data-ttu-id="0b690-104">Verifica se a sintaxe apropriada do separador de unidade (dois-pontos) foi feita mais corretamente, o que teve o efeito colateral de bloquear alguns caminhos de URI em algumas APIs de caminho SELECT em que foram toleradas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="0b690-104">Checks for proper drive separator (colon) syntax were made more correct, which had the side effect of blocking some URI paths in a few select Path APIs where they were previously tolerated.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0b690-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="0b690-105">Suggestion</span></span>

<span data-ttu-id="0b690-106">Ao passar um URI para as APIs afetadas, modifique a cadeia de caracteres para um caminho correto antes.</span><span class="sxs-lookup"><span data-stu-id="0b690-106">If passing a URI to affected APIs, modify the string to be a legal path first.</span></span>

- <span data-ttu-id="0b690-107">Remova o esquema de URLs manualmente (por exemplo, remover `file://` das URLs).</span><span class="sxs-lookup"><span data-stu-id="0b690-107">Remove the scheme from URLs manually (for example, remove `file://` from URLs).</span></span>

- <span data-ttu-id="0b690-108">Passe o URI para a <xref:System.Uri> classe e use <xref:System.Uri.LocalPath> .</span><span class="sxs-lookup"><span data-stu-id="0b690-108">Pass the URI to the <xref:System.Uri> class and use <xref:System.Uri.LocalPath>.</span></span>

<span data-ttu-id="0b690-109">Como alternativa, você pode recusar a normalização de novo caminho definindo a `Switch.System.IO.UseLegacyPathHandling` opção AppContext como `true` .</span><span class="sxs-lookup"><span data-stu-id="0b690-109">Alternatively, you can opt out of the new path normalization by setting the `Switch.System.IO.UseLegacyPathHandling` AppContext switch to `true`.</span></span>

| <span data-ttu-id="0b690-110">Nome</span><span class="sxs-lookup"><span data-stu-id="0b690-110">Name</span></span>    | <span data-ttu-id="0b690-111">Valor</span><span class="sxs-lookup"><span data-stu-id="0b690-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0b690-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="0b690-112">Scope</span></span>   | <span data-ttu-id="0b690-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="0b690-113">Edge</span></span>        |
| <span data-ttu-id="0b690-114">Versão</span><span class="sxs-lookup"><span data-stu-id="0b690-114">Version</span></span> | <span data-ttu-id="0b690-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="0b690-115">4.6.2</span></span>       |
| <span data-ttu-id="0b690-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="0b690-116">Type</span></span>    | <span data-ttu-id="0b690-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="0b690-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="0b690-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0b690-118">Affected APIs</span></span>

- <xref:System.IO.Path.GetDirectoryName(System.String)?displayProperty=nameWithType>
- <xref:System.IO.Path.GetPathRoot(System.String)?displayProperty=nameWithType>
