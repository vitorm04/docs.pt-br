---
title: Introdução ao objeto GlyphRun e ao elemento de glifos
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], Glyphs element
- Glyphs elements [WPF]
- GlyphRun object [WPF]
- text [WPF], glyphs
- glyphs [WPF]
- typography [WPF], GlyphRun object
ms.assetid: 746ca769-a331-4435-9b95-f72a883b67c1
ms.openlocfilehash: 5750177c03cf859ebb884c5774b7ded03fa60628
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547375"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="93113-102">Introdução ao objeto GlyphRun e ao elemento de glifos</span><span class="sxs-lookup"><span data-stu-id="93113-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="93113-103">Este tópico descreve o <xref:System.Windows.Media.GlyphRun> objeto e o <xref:System.Windows.Documents.Glyphs> elemento.</span><span class="sxs-lookup"><span data-stu-id="93113-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
  
<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="93113-104">Introdução ao GlyphRun</span><span class="sxs-lookup"><span data-stu-id="93113-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="93113-105"> fornece suporte avançado de texto incluindo marcação em nível de glifos com acesso direto a <xref:System.Windows.Documents.Glyphs> para clientes que desejam interceptar e persistir texto após a formatação.</span><span class="sxs-lookup"><span data-stu-id="93113-105"> provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="93113-106">Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="93113-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1.  <span data-ttu-id="93113-107">Exibição em tela de documentos de formato fixo.</span><span class="sxs-lookup"><span data-stu-id="93113-107">Screen display of fixed-format documents.</span></span>  
  
2.  <span data-ttu-id="93113-108">Cenários de impressão.</span><span class="sxs-lookup"><span data-stu-id="93113-108">Print scenarios.</span></span>  
  
    -   [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="93113-109"> como uma linguagem de impressora do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="93113-109"> as a device printer language.</span></span>  
  
    -   [!INCLUDE[TLA#tla_mxdw](../../../../includes/tlasharptla-mxdw-md.md)]<span data-ttu-id="93113-110">.</span><span class="sxs-lookup"><span data-stu-id="93113-110">.</span></span>  
  
    -   <span data-ttu-id="93113-111">A saída de drivers de impressão anteriores é de aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] para o formato fixo.</span><span class="sxs-lookup"><span data-stu-id="93113-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    -   <span data-ttu-id="93113-112">Formato do spool de impressão.</span><span class="sxs-lookup"><span data-stu-id="93113-112">Print spool format.</span></span>  
  
3.  <span data-ttu-id="93113-113">Representação de documentos de formato fixo, incluindo clientes de versões anteriores do [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] e outros dispositivos de computação.</span><span class="sxs-lookup"><span data-stu-id="93113-113">Fixed-format document representation, including clients for previous versions of [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] and other computing devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93113-114"><xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> são projetados para apresentação do documento de formato fixo e cenários de impressão.</span><span class="sxs-lookup"><span data-stu-id="93113-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="93113-115"> fornece vários elementos para layout geral e [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] cenários como <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="93113-115"> provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="93113-116">Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="93113-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="93113-117">O Objeto GlyphRun</span><span class="sxs-lookup"><span data-stu-id="93113-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="93113-118">O <xref:System.Windows.Media.GlyphRun> objeto representa uma sequência de glifos de uma única face de uma única fonte em um tamanho único e com um estilo de renderização único.</span><span class="sxs-lookup"><span data-stu-id="93113-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="93113-119"><xref:System.Windows.Media.GlyphRun> inclui ambos os detalhes da fonte como glifos <xref:System.Windows.Documents.Glyphs.Indices%2A> e posições glifo individuais.</span><span class="sxs-lookup"><span data-stu-id="93113-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="93113-120">Ele também inclui o original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] a execução foi gerada de informações de mapeamento de deslocamento de buffer de glifo de caracteres e sinalizadores por caracteres e por glifo de pontos de código.</span><span class="sxs-lookup"><span data-stu-id="93113-120">It also includes the original [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="93113-121"><xref:System.Windows.Media.GlyphRun> tem um alto nível correspondente <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="93113-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="93113-122"><xref:System.Windows.Documents.Glyphs> pode ser usado na árvore de elementos e no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] marcação para representar <xref:System.Windows.Media.GlyphRun> saída.</span><span class="sxs-lookup"><span data-stu-id="93113-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="93113-123">O Elemento Glyphs</span><span class="sxs-lookup"><span data-stu-id="93113-123">The Glyphs Element</span></span>  
 <span data-ttu-id="93113-124">O <xref:System.Windows.Documents.Glyphs> elemento representa a saída de um <xref:System.Windows.Media.GlyphRun> em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93113-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="93113-125">A seguinte sintaxe de marcação é usada para descrever o <xref:System.Windows.Documents.Glyphs> elemento.</span><span class="sxs-lookup"><span data-stu-id="93113-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="93113-126">As seguintes definições de propriedade correspondem aos quatro primeiros atributos na marcação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="93113-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="93113-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="93113-127">Property</span></span>|<span data-ttu-id="93113-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="93113-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="93113-129">Especifica um identificador de recurso: nome de arquivo da Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], ou uma referência de recurso no aplicativo .exe ou no contêiner.</span><span class="sxs-lookup"><span data-stu-id="93113-129">Specifies a resource identifier: file name, Web [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)], or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="93113-130">Especifica o tamanho da fonte em unidades de superfície de desenho (o padrão é 0,96 polegadas).</span><span class="sxs-lookup"><span data-stu-id="93113-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="93113-131">Especifica os sinalizadores para estilos em negrito e itálico.</span><span class="sxs-lookup"><span data-stu-id="93113-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="93113-132">Especifica o nível de layout bidirecional.</span><span class="sxs-lookup"><span data-stu-id="93113-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="93113-133">Valores pares e zero implicam um layout da esquerda para a direita; valores ímpares implicam um layout da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="93113-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="93113-134">Propriedade de índices</span><span class="sxs-lookup"><span data-stu-id="93113-134">Indices property</span></span>  
 <span data-ttu-id="93113-135">O <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade é uma cadeia de caracteres de especificações de glifo.</span><span class="sxs-lookup"><span data-stu-id="93113-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="93113-136">Quando uma sequência de glifos forma um único cluster, a especificação do primeiro glifo no cluster será precedida por uma especificação de quantos glifos e quantos pontos de código se combinam para formar o cluster.</span><span class="sxs-lookup"><span data-stu-id="93113-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="93113-137">O <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade coleta em uma cadeia de caracteres as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="93113-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
-   <span data-ttu-id="93113-138">Índices de glifo</span><span class="sxs-lookup"><span data-stu-id="93113-138">Glyph indices</span></span>  
  
-   <span data-ttu-id="93113-139">Larguras de avanço de glifo</span><span class="sxs-lookup"><span data-stu-id="93113-139">Glyph advance widths</span></span>  
  
-   <span data-ttu-id="93113-140">Combinando vetores de anexo de glifo</span><span class="sxs-lookup"><span data-stu-id="93113-140">Combining glyph attachment vectors</span></span>  
  
-   <span data-ttu-id="93113-141">Mapeamento de cluster de pontos de código para glifos</span><span class="sxs-lookup"><span data-stu-id="93113-141">Cluster mapping from code points to glyphs</span></span>  
  
-   <span data-ttu-id="93113-142">Sinalizadores de glifo</span><span class="sxs-lookup"><span data-stu-id="93113-142">Glyph flags</span></span>  
  
 <span data-ttu-id="93113-143">Cada especificação de glifo tem o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="93113-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="93113-144">Métricas de glifo</span><span class="sxs-lookup"><span data-stu-id="93113-144">Glyph Metrics</span></span>  
 <span data-ttu-id="93113-145">Cada glifo define métricas que especificam como ele se alinha com outros <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="93113-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="93113-146">O gráfico a seguir define as várias qualidades tipográficas de dois caracteres de glifo diferentes.</span><span class="sxs-lookup"><span data-stu-id="93113-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="93113-147">![Diagrama gráfico de medidas de glifo](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="93113-147">![Diagraph of glyph measurements](../../../../docs/framework/wpf/advanced/media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="93113-148">Marcação de glifos</span><span class="sxs-lookup"><span data-stu-id="93113-148">Glyphs Markup</span></span>  
 <span data-ttu-id="93113-149">O exemplo de código a seguir mostra como usar várias propriedades do <xref:System.Windows.Documents.Glyphs> elemento [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="93113-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="93113-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93113-150">See Also</span></span>  
 [<span data-ttu-id="93113-151">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="93113-151">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [<span data-ttu-id="93113-152">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="93113-152">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="93113-153">Texto</span><span class="sxs-lookup"><span data-stu-id="93113-153">Text</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)
