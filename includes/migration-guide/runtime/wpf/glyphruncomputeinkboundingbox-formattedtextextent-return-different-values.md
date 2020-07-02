---
ms.openlocfilehash: 00ffc782c9a15c0d88f797f52372b4658706b350
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619880"
---
### <a name="glyphruncomputeinkboundingbox-and-formattedtextextent-return-different-values-beginning-in-net-framework-45"></a><span data-ttu-id="2f8e4-101">GlyphRun.ComputeInkBoundingBox() e FormattedText.Extent retornam valores diferentes começando no .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2f8e4-101">GlyphRun.ComputeInkBoundingBox() and FormattedText.Extent return different values beginning in .NET Framework 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="2f8e4-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2f8e4-102">Details</span></span>

<span data-ttu-id="2f8e4-103">Foram feitas melhorias em <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> e <xref:System.Windows.Media.FormattedText.Extent> do .NET Framework 4.5 para resolver problemas em que as caixas eram muito pequenas para o glifos contidos em alguns casos no .NET Framework 4.0.</span><span class="sxs-lookup"><span data-stu-id="2f8e4-103">Improvements were made to <xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox> and <xref:System.Windows.Media.FormattedText.Extent> in the .NET Framework 4.5 to address issues where the boxes were too small for the contained glyphs in some cases in the .NET Framework 4.0.</span></span> <span data-ttu-id="2f8e4-104">Como resultado, algumas caixas delimitadoras serão maiores a partir do .NET Framework 4.5, resultando em diferenças sutis no layout da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2f8e4-104">As a result of this, some bounding boxes will be larger beginning in the .NET Framework 4.5, resulting in subtle differences in UI layout.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2f8e4-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2f8e4-105">Suggestion</span></span>

<span data-ttu-id="2f8e4-106">Lembre-se de que alguns tamanhos de caixa delimitadora do glifo aumentaram.</span><span class="sxs-lookup"><span data-stu-id="2f8e4-106">Be aware that some glyph bounding box sizes have increased.</span></span> <span data-ttu-id="2f8e4-107">Essas alterações geralmente aprimorarão a apresentação e os testes de caixa de clique, mas se o comportamento anterior (anterior ao .NET 4.5) for desejado, ele poderá ser aceito com a adição da seguinte entrada ao arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="2f8e4-107">These changes will usually improve presentation and hit box testing, but if the older (pre-.NET 4.5) behavior is desired, it can be opted into by adding the following entry to the app.config file:</span></span><pre><code class="lang-xml">&lt;appsettings&gt;&#13;&#10;&lt;add key=&quot;IncludeAllInkInBoundingBox&quot; value=&quot;false&quot;&gt;&#13;&#10;&lt;/appsettings&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="2f8e4-108">Name</span><span class="sxs-lookup"><span data-stu-id="2f8e4-108">Name</span></span>    | <span data-ttu-id="2f8e4-109">Valor</span><span class="sxs-lookup"><span data-stu-id="2f8e4-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2f8e4-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="2f8e4-110">Scope</span></span>   |<span data-ttu-id="2f8e4-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="2f8e4-111">Edge</span></span>|
|<span data-ttu-id="2f8e4-112">Versão</span><span class="sxs-lookup"><span data-stu-id="2f8e4-112">Version</span></span>|<span data-ttu-id="2f8e4-113">4.5</span><span class="sxs-lookup"><span data-stu-id="2f8e4-113">4.5</span></span>|
|<span data-ttu-id="2f8e4-114">Type</span><span class="sxs-lookup"><span data-stu-id="2f8e4-114">Type</span></span>|<span data-ttu-id="2f8e4-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="2f8e4-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2f8e4-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2f8e4-116">Affected APIs</span></span>

-<xref:System.Windows.Media.GlyphRun.ComputeInkBoundingBox?displayProperty=nameWithType></li><li><xref:System.Windows.Media.FormattedText.Extent?displayProperty=nameWithType></li></ul>|
