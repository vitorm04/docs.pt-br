---
title: Visão geral da geração de imagens
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- metadata [WPF], images
- displaying images [WPF]
- Imaging API [WPF]
- image metadata [WPF]
- converting images [WPF]
- encoding image formats [WPF]
- format decoding for images [WPF]
- painting with images [WPF]
- stretching images [WPF]
- images [WPF], about imaging
- format encoding for images [WPF]
- cropping images [WPF]
- decoding image formats [WPF]
- rotating images [WPF]
ms.assetid: 72aad87a-e6f3-4937-94cd-a18b7766e990
ms.openlocfilehash: b6fb530bbc4132b09cc17ad692e6e9e23cd75598
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671852"
---
# <a name="imaging-overview"></a>Visão geral da geração de imagens
Este tópico é uma introdução ao [!INCLUDE[TLA#tla_wic](../../../../includes/tlasharptla-wic-md.md)]. O [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] permite aos desenvolvedores exibir, transformar e formatar imagens.  

<a name="_wpfImaging"></a>   
## <a name="wpf-imaging-component"></a>Componente de geração de imagens do WPF  
 O [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] proporciona melhorias significativas em recursos de geração de imagens no [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]. Os recursos de geração de imagens, como a exibição de um bitmap ou o uso de uma imagem em um controle comum, eram dependentes do Microsoft Windows Graphics Device Interface (GDI) ou das bibliotecas do Microsoft Windows GDI+. Essas APIs fornecem funcionalidade de geração de imagens de linha de base, mas não têm recursos como suporte para extensibilidade de codec e suporte a imagens de alta fidelidade. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]foi projetado para superar as deficiências do GDI e do GDI+ e fornecer um novo conjunto de API para exibir e usar imagens em seus aplicativos.  
  
 Há duas maneiras de acessar a [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] API, um componente gerenciado e um componente não gerenciado. O componente não gerenciado fornece os recursos a seguir.  
  
- Modelo de extensibilidade para formatos de imagem novos ou proprietários.  
  
- Desempenho e segurança aprimorados em formatos de imagem nativa, incluindo bitmap ( [!INCLUDE[TLA#tla_jpegorg](../../../../includes/tlasharptla-jpegorg-md.md)]BMP [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)]) [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)], [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)],,,, Graphics Interchange Format (GIF) e ícone (. ico).  
  
- Preservação de dados de alta intensidade de bits de imagem de até 8 bits por canal (32 bits por pixel).  
  
- Dimensionamento, corte e rotações de imagem não destrutivos.  
  
- Gerenciamento de cores simplificado.  
  
- Suporte para metadados proprietários em arquivo.  
  
- O componente gerenciado utiliza a infraestrutura não gerenciada para fornecer integração perfeita de imagens com outros recursos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] como [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], animação e elementos gráficos. O componente gerenciado também se beneficia do modelo de extensibilidade do codec de imagem Windows Presentation Foundation (WPF), que permite o reconhecimento automático [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] de novos formatos de imagem em aplicativos.  
  
 A maior parte da API [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] gerenciada reside <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> no namespace, embora vários tipos <xref:System.Windows.Media.ImageBrush> importantes, como e <xref:System.Windows.Media.ImageDrawing> residem no <xref:System.Windows.Media?displayProperty=nameWithType> namespace e <xref:System.Windows.Controls.Image> residem no <xref:System.Windows.Controls?displayProperty=nameWithType> namespace.  
  
 Este tópico fornece informações adicionais sobre o componente gerenciado. Para obter mais informações sobre a API não gerenciada, consulte a documentação [não gerenciada do componente de imagem do WPF](/windows/desktop/wic/-wic-lh) .  
  
<a name="_imageformats"></a>   
## <a name="wpf-image-formats"></a>Formatos de imagem do WPF  
 Um codec é usado para decodificar ou codificar um formato de mídia específico. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]inclui um codec para formatos de [!INCLUDE[TLA2#tla_jpeg](../../../../includes/tla2sharptla-jpeg-md.md)]imagem [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)]BMP, [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)],, [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)],, GIF e ícone. Cada um desses codecs habilitam aplicativos a decodificar e, com exceção do ÍCONE, codificar seus respectivos formatos de imagem.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>é uma classe importante usada na decodificação e codificação de imagens. É o bloco de construção básico do pipeline do [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] e representa um conjunto de pixels único e constante em um determinado tamanho e resolução. Um <xref:System.Windows.Media.Imaging.BitmapSource> pode ser um quadro individual de uma imagem de vários quadros ou pode ser o resultado de uma transformação executada em um <xref:System.Windows.Media.Imaging.BitmapSource>. É o pai de muitas das principais classes usadas na geração de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] imagens <xref:System.Windows.Media.Imaging.BitmapFrame>, como.  
  
 Um <xref:System.Windows.Media.Imaging.BitmapFrame> é usado para armazenar os dados reais de bitmap de um formato de imagem. Muitos formatos de imagem dão suporte apenas <xref:System.Windows.Media.Imaging.BitmapFrame>a um único, embora formatos como [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] gif e suportem vários quadros por imagem. Os quadros são usados por decodificadores como dados de entrada e são passados aos codificadores para criar arquivos de imagem.  
  
 O exemplo a seguir demonstra como <xref:System.Windows.Media.Imaging.BitmapFrame> um é criado a <xref:System.Windows.Media.Imaging.BitmapSource> partir de um e adicionado [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] a uma imagem.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Decodificação de formato de imagem  
 A decodificação de imagem é a conversão de um formato de imagem em dados de imagem que podem ser usados pelo sistema. Dessa maneira, os dados de imagem podem ser usados para exibir, processar ou codificar para um formato diferente. A seleção do decodificador é com base no formato de imagem. A seleção de codec é automática, a menos que um determinado decodificador seja especificado. Os exemplos na seção [Exibindo imagens no WPF](#_displayingimages) demonstram a decodificação automática. Os decodificadores de formato personalizados desenvolvidos com interfaces [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] não gerenciadas e registrados automaticamente com o sistema participam da seleção do decodificador. Isso permite que os formatos personalizados sejam exibidos automaticamente em aplicativos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 O exemplo a seguir demonstra o uso de um decodificador de bitmap para decodificar uma imagem de formato BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Codificação de formato de imagem  
 A codificação de imagem é a conversão de dados de imagem em um formato de imagem específico. Dessa maneira, os dados de imagem codificados podem ser usados para criar novos arquivos de imagem. O [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] fornece codificadores para cada um dos formatos de imagem descritos acima.  
  
 O exemplo a seguir demonstra o uso de um codificador para salvar uma imagem de bitmap recém-criada.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>   
## <a name="displaying-images-in-wpf"></a>Exibindo imagens no WPF  
 Há várias maneiras de exibir uma imagem em um aplicativo Windows Presentation Foundation (WPF). As imagens podem ser exibidas usando <xref:System.Windows.Controls.Image> um controle, pintadas em um Visual <xref:System.Windows.Media.ImageBrush>usando um ou desenhadas usando um <xref:System.Windows.Media.ImageDrawing>.  
  
### <a name="using-the-image-control"></a>Usando o controle de imagem  
 <xref:System.Windows.Controls.Image>é um elemento de estrutura e a maneira primária de exibir imagens em aplicativos. No [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ,<xref:System.Windows.Controls.Image> o pode ser usado de duas maneiras: sintaxe de atributo ou sintaxe de propriedade. O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando a sintaxe de atributo e a sintaxe de marca de propriedade. Para obter mais informações sobre a sintaxe de atributo e a sintaxe de propriedade, consulte [Visão geral de propriedades de dependência](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Muitos dos exemplos usam um <xref:System.Windows.Media.Imaging.BitmapImage> objeto para fazer referência a um arquivo de imagem. <xref:System.Windows.Media.Imaging.BitmapImage>é um especialista <xref:System.Windows.Media.Imaging.BitmapSource> que é otimizado [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para carregar e é uma maneira fácil de exibir imagens como <xref:System.Windows.Controls.Image.Source%2A> o de <xref:System.Windows.Controls.Image> um controle.  
  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando código.  
  
> [!NOTE]
>  <xref:System.Windows.Media.Imaging.BitmapImage>implementa a <xref:System.ComponentModel.ISupportInitialize> interface para otimizar a inicialização em várias propriedades. As alterações de propriedade só podem ocorrer durante a inicialização do objeto. Chame <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> para sinalizar que a inicialização foi <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> iniciada e para sinalizar que a inicialização foi concluída. Depois de inicializado, as alterações de propriedade serão ignoradas.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Girar, converter e recortar imagens  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]permite que os usuários transformem imagens usando propriedades <xref:System.Windows.Media.Imaging.BitmapImage> de ou usando objetos <xref:System.Windows.Media.Imaging.BitmapSource> adicionais, como <xref:System.Windows.Media.Imaging.CroppedBitmap> ou <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>. Essas transformações de imagem podem ajustar a escala ou girar uma imagem, alterar o formato de pixel de uma imagem ou recortar uma imagem.  
  
 Rotações de imagem são executadas usando a <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> propriedade de <xref:System.Windows.Media.Imaging.BitmapImage>. As rotações só podem ser feitas em incrementos de 90 graus. No exemplo a seguir, uma imagem é girada em 90 graus.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 A conversão de uma imagem em um formato de pixel diferente, como escala <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>de cinza, é feita usando. Nos exemplos a seguir, uma imagem é convertida <xref:System.Windows.Media.PixelFormats.Gray4%2A>em.  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Para cortar uma imagem, seja a <xref:System.Windows.UIElement.Clip%2A> propriedade de <xref:System.Windows.Controls.Image> ou <xref:System.Windows.Media.Imaging.CroppedBitmap> pode ser usada. Normalmente, se você quiser apenas exibir uma parte de uma imagem, <xref:System.Windows.UIElement.Clip%2A> deve ser usado. Se você precisar codificar e salvar uma imagem cortada, o <xref:System.Windows.Media.Imaging.CroppedBitmap> deverá ser usado. No exemplo a seguir, uma imagem é cortada usando a propriedade Clip usando um <xref:System.Windows.Media.EllipseGeometry>.  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Alongando imagens  
 A <xref:System.Windows.Controls.Image.Stretch%2A> propriedade controla como uma imagem é ampliada para preencher seu contêiner. A <xref:System.Windows.Controls.Image.Stretch%2A> Propriedade aceita os seguintes valores, definidos <xref:System.Windows.Media.Stretch> pela enumeração:  
  
- <xref:System.Windows.Media.Stretch.None>: A imagem não é ampliada para preencher a área de saída. Se a imagem for maior que a área de saída, ela será desenhada na área de saída, recortando que não couber.  
  
- <xref:System.Windows.Media.Stretch.Fill>: A imagem é dimensionada para caber na área de saída. Como a altura e a largura da imagem têm a escala ajustada de forma independente, a taxa de proporção original da imagem pode não ser preservada. Ou seja, a imagem poderá ser distorcida para preencher completamente o contêiner de saída.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: A imagem é dimensionada de forma que caiba completamente na área de saída. A taxa de proporção da imagem é preservada.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: A imagem é dimensionada de forma que ela preencha completamente a área de saída enquanto preserva a taxa de proporção original da imagem.  
  
 O exemplo a seguir aplica cada uma das <xref:System.Windows.Media.Stretch> enumerações disponíveis a <xref:System.Windows.Controls.Image>um.  
  
 A imagem a seguir mostra a saída do exemplo e demonstra o efeito que as <xref:System.Windows.Controls.Image.Stretch%2A> diferentes configurações têm quando aplicadas a uma imagem.  
  
 ![Diferentes configurações de alongamento de TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Configurações diferentes de alongamento  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Pintura com imagens  
 As imagens também podem ser exibidas em um aplicativo pintando com <xref:System.Windows.Media.Brush>um. Os pincéis permitem que você pinte objetos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] com qualquer coisa, desde cores simples e sólidas a conjuntos complexos de padrões e imagens. Para pintar com imagens, use um <xref:System.Windows.Media.ImageBrush>. Um <xref:System.Windows.Media.ImageBrush> é um tipo de <xref:System.Windows.Media.TileBrush> que define seu conteúdo como uma imagem de bitmap. Um <xref:System.Windows.Media.ImageBrush> exibe uma única imagem, que é especificada por sua <xref:System.Windows.Media.ImageBrush.ImageSource%2A> propriedade. É possível controlar como a imagem é alongada, alinhada e organizada lado a lado, permitindo que você evite distorção e produza padrões e outros efeitos. A ilustração a seguir mostra alguns efeitos que podem ser obtidos com <xref:System.Windows.Media.ImageBrush>um.  
  
 ![Exemplos de saída de ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Os pincéis de imagem podem preencher formas, controles, texto e muito mais  
  
 O exemplo a seguir demonstra como pintar o plano de fundo de um botão com uma imagem <xref:System.Windows.Media.ImageBrush>usando um.  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Para obter informações adicionais <xref:System.Windows.Media.ImageBrush> sobre e pintar imagens [, consulte pintando com imagens, desenhos e visuais](painting-with-images-drawings-and-visuals.md).  
  
<a name="_metadata"></a>   
## <a name="image-metadata"></a>Metadados de imagem  
 Alguns arquivos de imagem contêm metadados que descrevem o conteúdo ou as características do arquivo. Por exemplo, a maioria das câmeras digitais criam imagens que contêm metadados sobre a marca e modelo da câmera usada para capturar a imagem. Cada formato de imagem manipula os metadados de maneira diferente, mas o [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] fornece uma maneira uniforme de armazenar e recuperar metadados para cada formato de imagem com suporte.  
  
 O acesso aos metadados é fornecido por <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> meio da propriedade <xref:System.Windows.Media.Imaging.BitmapSource> de um objeto. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>Retorna um <xref:System.Windows.Media.Imaging.BitmapMetadata> objeto que inclui todos os metadados contidos na imagem. Esses dados podem estar em um esquema de metadados ou em uma combinação de esquemas diferentes. [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)]o dá suporte aos seguintes esquemas de metadados de imagem: Arquivo de imagem intercambiável (EXIF), texto (dados textuais de png) [!INCLUDE[TLA#tla_ifd](../../../../includes/tlasharptla-ifd-md.md)], [!INCLUDE[TLA#tla_iptc](../../../../includes/tlasharptla-iptc-md.md)], e [!INCLUDE[TLA#tla_xmp](../../../../includes/tlasharptla-xmp-md.md)].  
  
 Para simplificar o processo de leitura de metadados, <xref:System.Windows.Media.Imaging.BitmapMetadata> o fornece várias propriedades nomeadas que podem ser acessadas <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A> <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>facilmente, <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>como, e. Muitas dessas propriedades nomeadas também podem ser usadas para gravar metadados. O suporte adicional para a leitura de metadados é fornecido pelo leitor de consulta de metadados. O <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> método é usado para recuperar um leitor de consulta de metadados, fornecendo uma consulta de cadeia de caracteres como *"/app1/exif/"* . No exemplo a seguir, <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> é usado para obter o texto armazenado no local *"/Text/Description"* .  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Para gravar metadados, usa-se um gravador de consulta de metadados. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>Obtém o gravador de consulta e define o valor desejado. No exemplo a seguir, <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> é usado para gravar o texto armazenado no local *"/Text/Description"* .  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>   
## <a name="codec-extensibility"></a>Extensibilidade de codec  
 Um recurso principal do [!INCLUDE[TLA2#tla_wic](../../../../includes/tla2sharptla-wic-md.md)] é o modelo de extensibilidade para novos codecs de imagem. Essas interfaces não gerenciadas permitem que os desenvolvedores de codec integrem os codecs com o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] para que novos formatos de imagem possam ser usados automaticamente por aplicativos do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
 Para obter um exemplo da API de extensibilidade, consulte o [codec de exemplo do Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Este exemplo demonstra como criar um decodificador e codificador para um formato de imagem personalizado.  
  
> [!NOTE]
>  O codec deve ser assinado digitalmente para que o sistema o reconheça.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Codec de exemplo do Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
