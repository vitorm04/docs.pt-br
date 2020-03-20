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
ms.openlocfilehash: 32e8ab7104b8ea2f985395065868ed154ca1e378
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181959"
---
# <a name="introduction-to-the-glyphrun-object-and-glyphs-element"></a><span data-ttu-id="64f3c-102">Introdução ao objeto GlyphRun e ao elemento de glifos</span><span class="sxs-lookup"><span data-stu-id="64f3c-102">Introduction to the GlyphRun Object and Glyphs Element</span></span>
<span data-ttu-id="64f3c-103">Este tópico descreve <xref:System.Windows.Media.GlyphRun> o <xref:System.Windows.Documents.Glyphs> objeto e o elemento.</span><span class="sxs-lookup"><span data-stu-id="64f3c-103">This topic describes the <xref:System.Windows.Media.GlyphRun> object and the <xref:System.Windows.Documents.Glyphs> element.</span></span>  

<a name="text_glyphrunovw_intro"></a>
## <a name="introduction-to-glyphrun"></a><span data-ttu-id="64f3c-104">Introdução ao GlyphRun</span><span class="sxs-lookup"><span data-stu-id="64f3c-104">Introduction to GlyphRun</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="64f3c-105">fornece suporte avançado de texto, incluindo marcação <xref:System.Windows.Documents.Glyphs> em nível de glifos com acesso direto para clientes que desejam interceptar e persistir texto após a formatação.</span><span class="sxs-lookup"><span data-stu-id="64f3c-105">provides advanced text support including glyph-level markup with direct access to <xref:System.Windows.Documents.Glyphs> for customers who want to intercept and persist text after formatting.</span></span> <span data-ttu-id="64f3c-106">Esses recursos dão suporte crítico aos diferentes requisitos de renderização de texto em cada um dos cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="64f3c-106">These features provide critical support for the different text rendering requirements in each of the following scenarios.</span></span>  
  
1. <span data-ttu-id="64f3c-107">Exibição em tela de documentos de formato fixo.</span><span class="sxs-lookup"><span data-stu-id="64f3c-107">Screen display of fixed-format documents.</span></span>  
  
2. <span data-ttu-id="64f3c-108">Cenários de impressão.</span><span class="sxs-lookup"><span data-stu-id="64f3c-108">Print scenarios.</span></span>  
  
    - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <span data-ttu-id="64f3c-109">como uma linguagem de impressora do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="64f3c-109">as a device printer language.</span></span>  
  
    - <span data-ttu-id="64f3c-110">Escritor de documentos Microsoft XPS.</span><span class="sxs-lookup"><span data-stu-id="64f3c-110">Microsoft XPS Document Writer.</span></span>  
  
    - <span data-ttu-id="64f3c-111">Drivers de impressora anteriores, saída de aplicativos Win32 para o formato fixo.</span><span class="sxs-lookup"><span data-stu-id="64f3c-111">Previous printer drivers, output from Win32 applications to the fixed format.</span></span>  
  
    - <span data-ttu-id="64f3c-112">Formato do spool de impressão.</span><span class="sxs-lookup"><span data-stu-id="64f3c-112">Print spool format.</span></span>  
  
3. <span data-ttu-id="64f3c-113">Representação de documentos em formato fixo, incluindo clientes para versões anteriores do Windows e outros dispositivos de computação.</span><span class="sxs-lookup"><span data-stu-id="64f3c-113">Fixed-format document representation, including clients for previous versions of Windows and other computing devices.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64f3c-114"><xref:System.Windows.Documents.Glyphs>e <xref:System.Windows.Media.GlyphRun> são projetados para apresentação de documentos em formato fixo e cenários de impressão.</span><span class="sxs-lookup"><span data-stu-id="64f3c-114"><xref:System.Windows.Documents.Glyphs> and <xref:System.Windows.Media.GlyphRun> are designed for fixed-format document presentation and print scenarios.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="64f3c-115">fornece vários elementos [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] para layout <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock>geral e cenários como e .</span><span class="sxs-lookup"><span data-stu-id="64f3c-115">provides several elements for general layout and [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scenarios such as <xref:System.Windows.Controls.Label> and <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="64f3c-116">Para obter mais [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] informações sobre layout e cenários, consulte a [Tipografia no WPF](typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="64f3c-116">For more information on layout and [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios, see the [Typography in WPF](typography-in-wpf.md).</span></span>  
  
<a name="text_glyphrunovw_glyphrunobject"></a>
## <a name="the-glyphrun-object"></a><span data-ttu-id="64f3c-117">O Objeto GlyphRun</span><span class="sxs-lookup"><span data-stu-id="64f3c-117">The GlyphRun Object</span></span>  
 <span data-ttu-id="64f3c-118">O <xref:System.Windows.Media.GlyphRun> objeto representa uma seqüência de glifos de uma única face de uma única fonte em um único tamanho, e com um único estilo de renderização.</span><span class="sxs-lookup"><span data-stu-id="64f3c-118">The <xref:System.Windows.Media.GlyphRun> object represents a sequence of glyphs from a single face of a single font at a single size, and with a single rendering style.</span></span>  
  
 <span data-ttu-id="64f3c-119"><xref:System.Windows.Media.GlyphRun>inclui ambos os detalhes da <xref:System.Windows.Documents.Glyphs.Indices%2A> fonte, como as posições do glifo e do glifo individual.</span><span class="sxs-lookup"><span data-stu-id="64f3c-119"><xref:System.Windows.Media.GlyphRun> includes both font details such as glyph <xref:System.Windows.Documents.Glyphs.Indices%2A> and individual glyph positions.</span></span> <span data-ttu-id="64f3c-120">Ele também inclui os pontos de código Unicode originais dos quais a execução foi gerada, informações de mapeamento de deslocamento de buffer de caractere para glifos, e sinalizadores por caractere e por glifos.</span><span class="sxs-lookup"><span data-stu-id="64f3c-120">It also includes the original Unicode code points the run was generated from, character-to-glyph buffer offset mapping information, and per-character and per-glyph flags.</span></span>  
  
 <span data-ttu-id="64f3c-121"><xref:System.Windows.Media.GlyphRun>tem um alto <xref:System.Windows.FrameworkElement>nível <xref:System.Windows.Documents.Glyphs>correspondente, .</span><span class="sxs-lookup"><span data-stu-id="64f3c-121"><xref:System.Windows.Media.GlyphRun> has a corresponding high-level <xref:System.Windows.FrameworkElement>, <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="64f3c-122"><xref:System.Windows.Documents.Glyphs>pode ser usado na árvore [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de elementos e na marcação para representar <xref:System.Windows.Media.GlyphRun> a saída.</span><span class="sxs-lookup"><span data-stu-id="64f3c-122"><xref:System.Windows.Documents.Glyphs> can be used in the element tree and in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup to represent <xref:System.Windows.Media.GlyphRun> output.</span></span>  
  
<a name="text_glyphrunovw_glyphselement"></a>
## <a name="the-glyphs-element"></a><span data-ttu-id="64f3c-123">O Elemento Glyphs</span><span class="sxs-lookup"><span data-stu-id="64f3c-123">The Glyphs Element</span></span>  
 <span data-ttu-id="64f3c-124">O <xref:System.Windows.Documents.Glyphs> elemento representa a <xref:System.Windows.Media.GlyphRun> saída [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]de a in .</span><span class="sxs-lookup"><span data-stu-id="64f3c-124">The <xref:System.Windows.Documents.Glyphs> element represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="64f3c-125">A seguinte sintaxe de marcação é usada para descrever o <xref:System.Windows.Documents.Glyphs> elemento.</span><span class="sxs-lookup"><span data-stu-id="64f3c-125">The following markup syntax is used to describe the <xref:System.Windows.Documents.Glyphs> element.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="64f3c-126">As seguintes definições de propriedade correspondem aos quatro primeiros atributos na marcação de exemplo.</span><span class="sxs-lookup"><span data-stu-id="64f3c-126">The following property definitions correspond to the first four attributes in the sample markup.</span></span>  
  
|<span data-ttu-id="64f3c-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="64f3c-127">Property</span></span>|<span data-ttu-id="64f3c-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="64f3c-128">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Documents.Glyphs.FontUri%2A>|<span data-ttu-id="64f3c-129">Especifica um identificador de recursos: nome do arquivo, uri (Web uniform resource identifier, identificador de recursos) ou referência de recursos no aplicativo .exe ou contêiner.</span><span class="sxs-lookup"><span data-stu-id="64f3c-129">Specifies a resource identifier: file name, Web uniform resource identifier (URI), or resource reference in the application .exe or container.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.FontRenderingEmSize%2A>|<span data-ttu-id="64f3c-130">Especifica o tamanho da fonte em unidades de superfície de desenho (o padrão é 0,96 polegadas).</span><span class="sxs-lookup"><span data-stu-id="64f3c-130">Specifies the font size in drawing surface units (default is .96 inches).</span></span>|  
|<xref:System.Windows.Documents.Glyphs.StyleSimulations%2A>|<span data-ttu-id="64f3c-131">Especifica os sinalizadores para estilos em negrito e itálico.</span><span class="sxs-lookup"><span data-stu-id="64f3c-131">Specifies flags for bold and Italic styles.</span></span>|  
|<xref:System.Windows.Documents.Glyphs.BidiLevel%2A>|<span data-ttu-id="64f3c-132">Especifica o nível de layout bidirecional.</span><span class="sxs-lookup"><span data-stu-id="64f3c-132">Specifies the bidirectional layout level.</span></span> <span data-ttu-id="64f3c-133">Valores pares e zero implicam um layout da esquerda para a direita; valores ímpares implicam um layout da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="64f3c-133">Even-numbered and zero values imply left-to-right layout; odd-numbered values imply right-to-left layout.</span></span>|  
  
<a name="text_glyphrunovw_indicesproperty"></a>
### <a name="indices-property"></a><span data-ttu-id="64f3c-134">Propriedade de índices</span><span class="sxs-lookup"><span data-stu-id="64f3c-134">Indices property</span></span>  
 <span data-ttu-id="64f3c-135">A <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade é uma série de especificações de glifos.</span><span class="sxs-lookup"><span data-stu-id="64f3c-135">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property is a string of glyph specifications.</span></span> <span data-ttu-id="64f3c-136">Quando uma sequência de glifos forma um único cluster, a especificação do primeiro glifo no cluster será precedida por uma especificação de quantos glifos e quantos pontos de código se combinam para formar o cluster.</span><span class="sxs-lookup"><span data-stu-id="64f3c-136">Where a sequence of glyphs forms a single cluster, the specification of the first glyph in the cluster is preceded by a specification of how many glyphs and how many code points combine to form the cluster.</span></span> <span data-ttu-id="64f3c-137">A <xref:System.Windows.Documents.Glyphs.Indices%2A> propriedade coleta em uma seqüência as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="64f3c-137">The <xref:System.Windows.Documents.Glyphs.Indices%2A> property collects in one string the following properties.</span></span>  
  
- <span data-ttu-id="64f3c-138">Índices de glifo</span><span class="sxs-lookup"><span data-stu-id="64f3c-138">Glyph indices</span></span>  
  
- <span data-ttu-id="64f3c-139">Larguras de avanço de glifo</span><span class="sxs-lookup"><span data-stu-id="64f3c-139">Glyph advance widths</span></span>  
  
- <span data-ttu-id="64f3c-140">Combinando vetores de anexo de glifo</span><span class="sxs-lookup"><span data-stu-id="64f3c-140">Combining glyph attachment vectors</span></span>  
  
- <span data-ttu-id="64f3c-141">Mapeamento de cluster de pontos de código para glifos</span><span class="sxs-lookup"><span data-stu-id="64f3c-141">Cluster mapping from code points to glyphs</span></span>  
  
- <span data-ttu-id="64f3c-142">Sinalizadores de glifo</span><span class="sxs-lookup"><span data-stu-id="64f3c-142">Glyph flags</span></span>  
  
 <span data-ttu-id="64f3c-143">Cada especificação de glifo tem o seguinte formato.</span><span class="sxs-lookup"><span data-stu-id="64f3c-143">Each glyph specification has the following form.</span></span>  
  
 `[GlyphIndex][,[Advance][,[uOffset][,[vOffset][,[Flags]]]]]`  
  
<a name="text_glyphrunovw_glyphmetrics"></a>
## <a name="glyph-metrics"></a><span data-ttu-id="64f3c-144">Métricas de glifo</span><span class="sxs-lookup"><span data-stu-id="64f3c-144">Glyph Metrics</span></span>  
 <span data-ttu-id="64f3c-145">Cada glifo define métricas que especificam como <xref:System.Windows.Documents.Glyphs>ele se alinha com outros .</span><span class="sxs-lookup"><span data-stu-id="64f3c-145">Each glyph defines metrics that specify how it aligns with other <xref:System.Windows.Documents.Glyphs>.</span></span> <span data-ttu-id="64f3c-146">O gráfico a seguir define as várias qualidades tipográficas de dois caracteres de glifo diferentes.</span><span class="sxs-lookup"><span data-stu-id="64f3c-146">The following graphic defines the various typographic qualities of two different glyph characters.</span></span>  
  
 <span data-ttu-id="64f3c-147">![Diagrama de medidas de glifo](./media/glyph-example.png "glyph_example")</span><span class="sxs-lookup"><span data-stu-id="64f3c-147">![Diagraph of glyph measurements](./media/glyph-example.png "glyph_example")</span></span>  
  
<a name="text_glyphrunovw_glyphsmarkup"></a>
## <a name="glyphs-markup"></a><span data-ttu-id="64f3c-148">Marcação de glifos</span><span class="sxs-lookup"><span data-stu-id="64f3c-148">Glyphs Markup</span></span>  
 <span data-ttu-id="64f3c-149">O exemplo de código a seguir <xref:System.Windows.Documents.Glyphs> mostra [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]como usar várias propriedades do elemento em .</span><span class="sxs-lookup"><span data-stu-id="64f3c-149">The following code example shows how to use various properties of the <xref:System.Windows.Documents.Glyphs> element in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="64f3c-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="64f3c-150">See also</span></span>

- [<span data-ttu-id="64f3c-151">Tipografia no WPF</span><span class="sxs-lookup"><span data-stu-id="64f3c-151">Typography in WPF</span></span>](typography-in-wpf.md)
- [<span data-ttu-id="64f3c-152">Documentos no WPF</span><span class="sxs-lookup"><span data-stu-id="64f3c-152">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="64f3c-153">Texto</span><span class="sxs-lookup"><span data-stu-id="64f3c-153">Text</span></span>](optimizing-performance-text.md)
