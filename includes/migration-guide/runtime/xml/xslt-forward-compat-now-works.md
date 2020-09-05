---
ms.openlocfilehash: 8c8477ae3719cfcc2060459ba85bcc9e76f11c41
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497661"
---
### <a name="xslt-forward-compat-now-works"></a><span data-ttu-id="fc553-101">Compatibilidade com versões posteriores do XSLT agora funciona</span><span class="sxs-lookup"><span data-stu-id="fc553-101">XSLT forward compat now works</span></span>

#### <a name="details"></a><span data-ttu-id="fc553-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fc553-102">Details</span></span>

<span data-ttu-id="fc553-103">No .NET Framework 4, a compatibilidade com versões posteriores do XSLT 1.0 tinha os seguintes problemas:</span><span class="sxs-lookup"><span data-stu-id="fc553-103">In the .NET Framework 4, XSLT 1.0 forward compatibility had the following issues:</span></span><ul><li><span data-ttu-id="fc553-104">O carregamento de uma folha de estilos falhava se sua versão era definida como 2.0 e o analisador encontrava uma compilação XSLT 1.0 não reconhecida.</span><span class="sxs-lookup"><span data-stu-id="fc553-104">Loading a style sheet failed if its version was set to 2.0 and the parser encountered an unrecognized XSLT 1.0 construct.</span></span></li><li><span data-ttu-id="fc553-105">A construção<code>xsl:sort</code> falhava ao classificar os dados se a versão de folha de estilo era definida como 1.1.</span><span class="sxs-lookup"><span data-stu-id="fc553-105">The <code>xsl:sort</code> construct failed to sort data if the style sheet version was set to 1.1.</span></span></li></ul><span data-ttu-id="fc553-106">No .NET Framework 4.5, esses problemas foram corrigidos, e o modo de compatibilidade com versões posteriores do XSLT 1.0 funciona corretamente.</span><span class="sxs-lookup"><span data-stu-id="fc553-106">In the .NET Framework 4.5, these issues have been fixed, and XSLT 1.0 forward compatibility mode works properly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fc553-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fc553-107">Suggestion</span></span>

<span data-ttu-id="fc553-108">A maioria dos aplicativos não deve ser afetada, mas os dados serão classificados diferentemente em alguns casos agora que xsl:sort é respeitado.</span><span class="sxs-lookup"><span data-stu-id="fc553-108">Most apps should be unaffected, however data will be sorted differently in some cases now that xsl:sort is respected.</span></span> <span data-ttu-id="fc553-109">Se <code>xsl:sort</code> for usado em folhas de estilo 1.1, verifique se os aplicativos dependem da ordem sem classificação dos dados.</span><span class="sxs-lookup"><span data-stu-id="fc553-109">If <code>xsl:sort</code> is used in 1.1 style sheets, confirm that apps were not depending on the unsorted order of data.</span></span> <span data-ttu-id="fc553-110">Se os aplicativos dependerem do comportamento de classificação de 4.0, remova <code>xsl:sort</code> da folha de estilos.</span><span class="sxs-lookup"><span data-stu-id="fc553-110">If apps rely on the 4.0 sorting behavior, remove <code>xsl:sort</code> from the style sheet.</span></span>

| <span data-ttu-id="fc553-111">Nome</span><span class="sxs-lookup"><span data-stu-id="fc553-111">Name</span></span>    | <span data-ttu-id="fc553-112">Valor</span><span class="sxs-lookup"><span data-stu-id="fc553-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fc553-113">Escopo</span><span class="sxs-lookup"><span data-stu-id="fc553-113">Scope</span></span>   |<span data-ttu-id="fc553-114">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="fc553-114">Edge</span></span>|
|<span data-ttu-id="fc553-115">Versão</span><span class="sxs-lookup"><span data-stu-id="fc553-115">Version</span></span>|<span data-ttu-id="fc553-116">4.5</span><span class="sxs-lookup"><span data-stu-id="fc553-116">4.5</span></span>|
|<span data-ttu-id="fc553-117">Tipo</span><span class="sxs-lookup"><span data-stu-id="fc553-117">Type</span></span>|<span data-ttu-id="fc553-118">Runtime</span><span class="sxs-lookup"><span data-stu-id="fc553-118">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fc553-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fc553-119">Affected APIs</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Xml.Xsl.XslCompiledTransform`

-->
