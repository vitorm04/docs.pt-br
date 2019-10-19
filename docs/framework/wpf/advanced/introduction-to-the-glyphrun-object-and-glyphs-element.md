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
ms.openlocfilehash: 2f7bb3fb4f28b063c78dde9f9f354b38a5e707f3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581901"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="a0db6-102">Introdução ao objeto GlyphRun e ao elemento de glifos</span><span class="sxs-lookup"><span data-stu-id="a0db6-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="a0db6-103">Este tópico descreve o objeto <xref:System.Windows.Media.GlyphRun> e o elemento <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="a0db6-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>   
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="a0db6-104">Introdução ao GlyphRun</span><span class="sxs-lookup"><span data-stu-id="a0db6-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="a0db6-105">fornece suporte de texto avançado, incluindo marcação de nível de glifo com acesso direto a <xref:System.Windows.Documents.Glyphs> para clientes que desejam interceptar e persistir texto após a formatação.</span><span class="sxs-lookup"><span data-stu-id="a0db6-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="a0db6-106">Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0db6-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="a0db6-107">Exibição em tela de documentos de formato fixo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="a0db6-108">Cenários de impressão.</span><span class="sxs-lookup"><span data-stu-id="a0db6-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="a0db6-109">como uma linguagem de impressora do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="a0db6-110">Microsoft XPS Document Writer.</span><span class="sxs-lookup"><span data-stu-id="a0db6-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="a0db6-111">A saída de drivers de impressão anteriores é de aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] para o formato fixo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-111">Previous printer drivers, output from [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="a0db6-112">Formato do spool de impressão.</span><span class="sxs-lookup"><span data-stu-id="a0db6-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="a0db6-113">Representação de documento de formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.</span><span class="sxs-lookup"><span data-stu-id="a0db6-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0db6-114"><xref:System.Windows.Documents.Glyphs> e <xref:System.Windows.Media.GlyphRun> são projetados para cenários de impressão e de apresentação de documentos de formato fixo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> <span data-ttu-id="a0db6-115">o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece vários elementos para o layout geral e cenários de [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], como <xref:System.Windows.Controls.Label> e <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="a0db6-115">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="a0db6-116">Para mais informações sobre layout e cenários [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], consulte [Tipografia no WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="a0db6-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>   
## <a name="the-glyphrun-object"></a><span data-ttu-id="a0db6-117">O Objeto GlyphRun</span><span class="sxs-lookup"><span data-stu-id="a0db6-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="a0db6-118">O objeto <xref:System.Windows.Media.GlyphRun> representa uma sequência de glifos de uma única face de uma única fonte em um único tamanho e com um único estilo de renderização.</span><span class="sxs-lookup"><span data-stu-id="a0db6-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="a0db6-119"><xref:System.Windows.Media.GlyphRun> inclui os detalhes da fonte, como glifo <xref:System.Windows.Documents.Glyphs.Indices%2A> e posições de glifo individuais.</span><span class="sxs-lookup"><span data-stu-id="a0db6-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="a0db6-120">Ele também inclui os pontos de código Unicode originais para os quais a execução foi gerada, informações de mapeamento de deslocamento de buffer de caractere para glifo e sinalizadores por caractere e por glifo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="a0db6-121"><xref:System.Windows.Media.GlyphRun> tem uma <xref:System.Windows.FrameworkElement> de alto nível correspondente, <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="a0db6-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="a0db6-122"><xref:System.Windows.Documents.Glyphs> pode ser usada na árvore de elementos e na marcação [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para representar <xref:System.Windows.Media.GlyphRun> saída.</span><span class="sxs-lookup"><span data-stu-id="a0db6-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>   
## <a name="the-glyphs-element"></a><span data-ttu-id="a0db6-123">O Elemento Glyphs</span><span class="sxs-lookup"><span data-stu-id="a0db6-123">The Glyphs Element</span></span>  
 <span data-ttu-id="a0db6-124">O elemento <xref:System.Windows.Documents.Glyphs> representa a saída de um <xref:System.Windows.Media.GlyphRun> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0db6-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="a0db6-125">A sintaxe de marcação a seguir é usada para descrever o elemento <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="a0db6-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="a0db6-126">As seguintes definições de propriedade correspondem aos quatro primeiros atributos na marcação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="a0db6-127">propriedade</span><span class="sxs-lookup"><span data-stu-id="a0db6-127">Property</span></span>|<span data-ttu-id="a0db6-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0db6-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="a0db6-129">Especifica um identificador de recurso: nome do arquivo, URI (Uniform Resource Identifier) da Web ou referência de recurso no Application. exe ou no contêiner.</span><span class="sxs-lookup"><span data-stu-id="a0db6-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="a0db6-130">Especifica o tamanho da fonte em unidades de superfície de desenho (o padrão é 0,96 polegadas).</span><span class="sxs-lookup"><span data-stu-id="a0db6-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="a0db6-131">Especifica os sinalizadores para estilos em negrito e itálico.</span><span class="sxs-lookup"><span data-stu-id="a0db6-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="a0db6-132">Especifica o nível de layout bidirecional.</span><span class="sxs-lookup"><span data-stu-id="a0db6-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="a0db6-133">Valores pares e zero implicam um layout da esquerda para a direita; valores ímpares implicam um layout da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="a0db6-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>   
### <a name="indices-property"></a><span data-ttu-id="a0db6-134">Propriedade de índices</span><span class="sxs-lookup"><span data-stu-id="a0db6-134">Indices property</span></span>  
 <span data-ttu-id="a0db6-135">A propriedade <xref:System.Windows.Documents.Glyphs.Indices%2A> é uma cadeia de especificações de glifo.</span><span class="sxs-lookup"><span data-stu-id="a0db6-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="a0db6-136">Quando uma sequência de glifos forma um único cluster, a especificação do primeiro glifo no cluster será precedida por uma especificação de quantos glifos e quantos pontos de código se combinam para formar o cluster.</span><span class="sxs-lookup"><span data-stu-id="a0db6-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="a0db6-137">A propriedade <xref:System.Windows.Documents.Glyphs.Indices%2A> coleta em uma cadeia de caracteres as propriedades a seguir.</span><span class="sxs-lookup"><span data-stu-id="a0db6-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="a0db6-138">Índices de glifo</span><span class="sxs-lookup"><span data-stu-id="a0db6-138">Glyph indices</span></span>  
  
- <span data-ttu-id="a0db6-139">Larguras de avanço de glifo</span><span class="sxs-lookup"><span data-stu-id="a0db6-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="a0db6-140">Combinando vetores de anexo de glifo</span><span class="sxs-lookup"><span data-stu-id="a0db6-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="a0db6-141">Mapeamento de cluster de pontos de código para glifos</span><span class="sxs-lookup"><span data-stu-id="a0db6-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="a0db6-142">Sinalizadores de glifo</span><span class="sxs-lookup"><span data-stu-id="a0db6-142">Glyph flags</span></span>  
  
 <span data-ttu-id="a0db6-143">Cada especificação de glifo tem o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="a0db6-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>   
## <a name="glyph-metrics"></a><span data-ttu-id="a0db6-144">Métricas de glifo</span><span class="sxs-lookup"><span data-stu-id="a0db6-144">Glyph Metrics</span></span>  
 <span data-ttu-id="a0db6-145">Cada glifo define as métricas que especificam como ela se alinha com outras <xref:System.Windows.Documents.Glyphs>.</span><span class="sxs-lookup"><span data-stu-id="a0db6-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="a0db6-146">O gráfico a seguir define as várias qualidades tipográficas de dois caracteres de glifo diferentes.</span><span class="sxs-lookup"><span data-stu-id="a0db6-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="a0db6-147">![Diagraph de medidas de glifo](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="a0db6-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>   
## <a name="glyphs-markup"></a><span data-ttu-id="a0db6-148">Marcação de glifos</span><span class="sxs-lookup"><span data-stu-id="a0db6-148">Glyphs Markup</span></span>  
 <span data-ttu-id="a0db6-149">O exemplo de código a seguir mostra como usar várias propriedades do elemento <xref:System.Windows.Documents.Glyphs> no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0db6-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a0db6-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0db6-150">See also</span></span>

- [<span data-ttu-id="a0db6-151">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="a0db6-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="a0db6-152">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="a0db6-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="a0db6-153">Texto</span><span class="sxs-lookup"><span data-stu-id="a0db6-153">Text</span></span>](optimizing-performance-text.md)
