---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619911"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="5026d-101">Compatibilidade com versões posteriores do XSLT agora funciona</span><span class="sxs-lookup"><span data-stu-id="5026d-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="5026d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5026d-102">Details</span></span>

<span data-ttu-id="5026d-103">No .NET Framework 4, a compatibilidade com versões posteriores do XSLT 1.0 tinha os seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="5026d-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="5026d-104">O carregamento de uma folha de estilos falhava se sua versão era definida como 2.0 e o analisador encontrava uma compilação XSLT 1.0 não reconhecida.</span><span class="sxs-lookup"><span data-stu-id="5026d-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="5026d-105">A construção<code>xsl:sort</code> falhava ao classificar os dados se a versão de folha de estilo era definida como 1.1.</span><span class="sxs-lookup"><span data-stu-id="5026d-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="5026d-106">No .NET Framework 4.5, esses problemas foram corrigidos, e o modo de compatibilidade com versões posteriores do XSLT 1.0 funciona corretamente.</span><span class="sxs-lookup"><span data-stu-id="5026d-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5026d-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="5026d-107">Suggestion</span></span>

<span data-ttu-id="5026d-108">A maioria dos aplicativos não deve ser afetada, mas os dados serão classificados diferentemente em alguns casos agora que xsl:sort é respeitado.</span><span class="sxs-lookup"><span data-stu-id="5026d-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="5026d-109">Se <code>xsl:sort</code> for usado em folhas de estilo 1.1, verifique se os aplicativos dependem da ordem sem classificação dos dados.</span><span class="sxs-lookup"><span data-stu-id="5026d-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="5026d-110">Se os aplicativos dependerem do comportamento de classificação de 4.0, remova <code>xsl:sort</code> da folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="5026d-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="5026d-111">Name</span><span class="sxs-lookup"><span data-stu-id="5026d-111">Name</span></span>    | <span data-ttu-id="5026d-112">Valor</span><span class="sxs-lookup"><span data-stu-id="5026d-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5026d-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="5026d-113">Scope</span></span>   |<span data-ttu-id="5026d-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="5026d-114">Edge</span></span>|
|<span data-ttu-id="5026d-115">Versão</span><span class="sxs-lookup"><span data-stu-id="5026d-115">Version</span></span>|<span data-ttu-id="5026d-116">4.5</span><span class="sxs-lookup"><span data-stu-id="5026d-116">4.5</span></span>|
|<span data-ttu-id="5026d-117">Type</span><span class="sxs-lookup"><span data-stu-id="5026d-117">Type</span></span>|<span data-ttu-id="5026d-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="5026d-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5026d-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="5026d-119">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
