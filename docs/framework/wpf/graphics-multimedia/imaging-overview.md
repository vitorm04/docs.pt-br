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
ms.openlocfilehash: 3365c35e3e7b7fe5c0be48a65d7a14da0882c90e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186688"
---
# <a name="imaging-overview"></a>Visão geral da geração de imagens
Este tópico fornece uma introdução ao Microsoft Windows Presentation Foundation Imaging Component. O WPF Imaging permite que os desenvolvedores exibam, transformem e formatarem imagens.  

## <a name="wpf-imaging-component"></a>Componente de geração de imagens do WPF  
 O WPF Imaging fornece melhorias significativas nos recursos de imagem dentro do Microsoft Windows. Os recursos de imagem, como exibir um bitmap ou usar uma imagem em um controle comum, eram anteriormente dependentes das bibliotecas GDI (Microsoft Windows Graphics Device Interface, interface de dispositivos gráficos) ou Microsoft Windows GDI+. Essas API fornecem funcionalidade de imagem de linha de base, mas carecem de recursos como suporte para extensibilidade de codec e suporte a imagens de alta fidelidade. O WPF Imaging foi projetado para superar as deficiências do GDI e GDI+ e fornecer um novo conjunto de API para exibir e usar imagens dentro de seus aplicativos.  
  
 Existem duas maneiras de acessar a API de imagem WPF, um componente gerenciado e um componente não gerenciado. O componente não gerenciado fornece os recursos a seguir.  
  
- Modelo de extensibilidade para formatos de imagem novos ou proprietários.  
  
- Desempenho e segurança aprimorados em formatos de imagem nativa, incluindo bitmap (BMP), Joint Photographics Experts Group (JPEG), Portable Network Graphics (PNG), Tagged Image File Format (TIFF), Microsoft Windows Media Photo, Graphics Interchange Format (GIF), e ícone (.ico).  
  
- Preservação de dados de alta intensidade de bits de imagem de até 8 bits por canal (32 bits por pixel).  
  
- Dimensionamento, corte e rotações de imagem não destrutivos.  
  
- Gerenciamento de cores simplificado.  
  
- Suporte para metadados proprietários em arquivo.  
  
- O componente gerenciado utiliza a infra-estrutura não gerenciada para fornecer integração perfeita de imagens com outros recursos do WPF, como [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]animação e gráficos. O componente gerenciado também se beneficia do modelo de extensibilidade de codec de imagem do Windows Presentation Foundation (WPF), que permite o reconhecimento automático de novos formatos de imagem em aplicativos WPF.  
  
 A maioria da API de imagem WPF <xref:System.Windows.Media.Imaging?displayProperty=nameWithType> gerenciada reside no namespace, embora vários tipos importantes, como <xref:System.Windows.Media.ImageBrush> e <xref:System.Windows.Media.ImageDrawing> residam no <xref:System.Windows.Media?displayProperty=nameWithType> namespace e <xref:System.Windows.Controls.Image> resida no <xref:System.Windows.Controls?displayProperty=nameWithType> namespace.  
  
 Este tópico fornece informações adicionais sobre o componente gerenciado. Para obter mais informações sobre a API não gerenciada, consulte a documentação [do componente de imagem WPF não gerenciado.](/windows/desktop/wic/-wic-lh)  
  
<a name="_imageformats"></a>
## <a name="wpf-image-formats"></a>Formatos de imagem do WPF  

 Um codec é usado para decodificar ou codificar um formato de mídia específico. O WPF Imaging inclui um codec para os formatos de imagem BMP, JPEG, PNG, TIFF, Windows Media Photo, GIF e ICON. Cada um desses codecs habilitam aplicativos a decodificar e, com exceção do ÍCONE, codificar seus respectivos formatos de imagem.  
  
 <xref:System.Windows.Media.Imaging.BitmapSource>é uma classe importante usada na decodificação e codificação de imagens. É o bloco básico de construção do gasoduto WPF Imaging e representa um único conjunto constante de pixels com um certo tamanho e resolução. A <xref:System.Windows.Media.Imaging.BitmapSource> pode ser um quadro individual de uma imagem de quadro múltiplo, <xref:System.Windows.Media.Imaging.BitmapSource>ou pode ser o resultado de uma transformação realizada em um . É o pai de muitas das classes primárias <xref:System.Windows.Media.Imaging.BitmapFrame>utilizadas na imagem do WPF, tais como .  
  
 A <xref:System.Windows.Media.Imaging.BitmapFrame> é usado para armazenar os dados reais do bitmap de um formato de imagem. Muitos formatos de imagem <xref:System.Windows.Media.Imaging.BitmapFrame>suportam apenas um único , embora formatos como GIF e TIFF suportem vários quadros por imagem. Os quadros são usados por decodificadores como dados de entrada e são passados aos codificadores para criar arquivos de imagem.  
  
 O exemplo a <xref:System.Windows.Media.Imaging.BitmapFrame> seguir demonstra como <xref:System.Windows.Media.Imaging.BitmapSource> um é criado a partir de um e, em seguida, adicionado a uma imagem TIFF.  
  
 [!code-csharp[BitmapFrameExample#10](~/samples/snippets/csharp/VS_Snippets_Wpf/BitmapFrameExample/CSharp/BitmapFrame.cs#10)]
 [!code-vb[BitmapFrameExample#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitmapFrameExample/VB/BitmapFrame.vb#10)]  
  
### <a name="image-format-decoding"></a>Decodificação de formato de imagem  
 A decodificação de imagem é a conversão de um formato de imagem em dados de imagem que podem ser usados pelo sistema. Dessa maneira, os dados de imagem podem ser usados para exibir, processar ou codificar para um formato diferente. A seleção do decodificador é com base no formato de imagem. A seleção de codec é automática, a menos que um determinado decodificador seja especificado. Os exemplos na seção [Exibindo imagens no WPF](#_displayingimages) demonstram a decodificação automática. Decodificadores de formato personalizado desenvolvidos usando as interfaces de imagem WPF não gerenciadas e registrados no sistema participam automaticamente da seleção do decodificador. Isso permite que formatos personalizados sejam exibidos automaticamente em aplicativos WPF.  
  
 O exemplo a seguir demonstra o uso de um decodificador de bitmap para decodificar uma imagem de formato BMP.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
### <a name="image-format-encoding"></a>Codificação de formato de imagem  
 A codificação de imagem é a conversão de dados de imagem em um formato de imagem específico. Dessa maneira, os dados de imagem codificados podem ser usados para criar novos arquivos de imagem. O WPF Imaging fornece codificadores para cada um dos formatos de imagem descritos acima.  
  
 O exemplo a seguir demonstra o uso de um codificador para salvar uma imagem de bitmap recém-criada.  
  
 [!code-cpp[BmpBitmapDecoderEncoder#3](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#3)]
 [!code-csharp[BmpBitmapDecoderEncoder#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#3)]
 [!code-vb[BmpBitmapDecoderEncoder#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#3)]  
  
<a name="_displayingimages"></a>
## <a name="displaying-images-in-wpf"></a>Exibindo imagens no WPF  
 Existem várias maneiras de exibir uma imagem em um aplicativo WPF (Windows Presentation Foundation). As imagens podem <xref:System.Windows.Controls.Image> ser exibidas usando um <xref:System.Windows.Media.ImageBrush>controle, pintadas <xref:System.Windows.Media.ImageDrawing>em um visual usando um , ou desenhado susceptino de usar um .  
  
### <a name="using-the-image-control"></a>Usando o controle de imagem  
 <xref:System.Windows.Controls.Image>é um elemento-quadro e a principal maneira de exibir imagens em aplicativos. Em [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.Image> , pode ser usado de duas maneiras; sintaxe de atributo ou sintaxe patrimonial. O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando a sintaxe de atributo e a sintaxe de marca de propriedade. Para obter mais informações sobre a sintaxe de atributo e a sintaxe de propriedade, consulte [Visão geral de propriedades de dependência](../advanced/dependency-properties-overview.md).  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
 Muitos dos exemplos usam <xref:System.Windows.Media.Imaging.BitmapImage> um objeto para referenciar um arquivo de imagem. <xref:System.Windows.Media.Imaging.BitmapImage>é uma <xref:System.Windows.Media.Imaging.BitmapSource> especializada que é [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] otimizada para carregamento e é <xref:System.Windows.Controls.Image.Source%2A> uma <xref:System.Windows.Controls.Image> maneira fácil de exibir imagens como o de um controle.  
  
 O exemplo a seguir mostra como renderizar uma imagem de 200 pixels de largura usando código.  
  
> [!NOTE]
> <xref:System.Windows.Media.Imaging.BitmapImage>implementa <xref:System.ComponentModel.ISupportInitialize> a interface para otimizar a inicialização em várias propriedades. As alterações de propriedade só podem ocorrer durante a inicialização do objeto. Chamada <xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A> para sinalizar que a <xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A> inicialização começou e para sinalizar que a inicialização foi concluída. Depois de inicializado, as alterações de propriedade serão ignoradas.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
#### <a name="rotating-converting-and-cropping-images"></a>Girar, converter e recortar imagens  
 O WPF permite que os <xref:System.Windows.Media.Imaging.BitmapImage> usuários transformem <xref:System.Windows.Media.Imaging.BitmapSource> imagens <xref:System.Windows.Media.Imaging.CroppedBitmap> <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>usando propriedades ou usando objetos adicionais, como ou . Essas transformações de imagem podem ajustar a escala ou girar uma imagem, alterar o formato de pixel de uma imagem ou recortar uma imagem.  
  
 As rotações de <xref:System.Windows.Media.Imaging.BitmapImage.Rotation%2A> imagem <xref:System.Windows.Media.Imaging.BitmapImage>são realizadas usando a propriedade de . As rotações só podem ser feitas em incrementos de 90 graus. No exemplo a seguir, uma imagem é girada em 90 graus.  
  
 [!code-xaml[ImageElementExample#TransformedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml#transformedxaml2)]  
  
 [!code-csharp[ImageElementExample#TransformedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/TransformedImageExample.xaml.cs#transformedcsharp1)]
 [!code-vb[ImageElementExample#TransformedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/TransformedImageExample.xaml.vb#transformedcsharp1)]  
  
 A conversão de uma imagem para um formato <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>de pixel diferente, como a escala de cinza, é feita usando . Nos exemplos a seguir, uma imagem <xref:System.Windows.Media.PixelFormats.Gray4%2A>é convertida em .  
  
 [!code-xaml[ImageElementExample_snip#ConvertedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml#convertedxaml2)]  
  
 [!code-csharp[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/FormatConvertedExample.xaml.cs#convertedcsharp1)]
 [!code-vb[ImageElementExample_snip#ConvertedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/FormatConvertedExample.xaml.vb#convertedcsharp1)]  
  
 Para cortar uma imagem, <xref:System.Windows.Controls.Image> seja <xref:System.Windows.Media.Imaging.CroppedBitmap> a <xref:System.Windows.UIElement.Clip%2A> propriedade ou pode ser usada. Normalmente, se você quiser apenas exibir uma <xref:System.Windows.UIElement.Clip%2A> parte de uma imagem, deve ser usado. Se você precisar codificar e salvar <xref:System.Windows.Media.Imaging.CroppedBitmap> uma imagem cortada, a deve ser usada. No exemplo a seguir, uma imagem é <xref:System.Windows.Media.EllipseGeometry>cortada usando a propriedade Clip usando um .  
  
 [!code-xaml[ImageElementExample_snip#CroppedXAMLUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml#croppedxamlusingclip1)]  
  
 [!code-csharp[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/CroppedImageExample.xaml.cs#croppedcsharpusingclip1)]
 [!code-vb[ImageElementExample_snip#CroppedCSharpUsingClip1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/CroppedImageExample.xaml.vb#croppedcsharpusingclip1)]  
  
#### <a name="stretching-images"></a>Alongando imagens  
 A <xref:System.Windows.Controls.Image.Stretch%2A> propriedade controla como uma imagem é esticada para encher seu recipiente. A <xref:System.Windows.Controls.Image.Stretch%2A> propriedade aceita os seguintes <xref:System.Windows.Media.Stretch> valores, definidos pela enumeração:  
  
- <xref:System.Windows.Media.Stretch.None>: A imagem não é esticada para preencher a área de saída. Se a imagem for maior que a área de saída, ela será desenhada na área de saída, recortando que não couber.  
  
- <xref:System.Windows.Media.Stretch.Fill>: A imagem é dimensionada para se adequar à área de saída. Como a altura e a largura da imagem têm a escala ajustada de forma independente, a taxa de proporção original da imagem pode não ser preservada. Ou seja, a imagem poderá ser distorcida para preencher completamente o contêiner de saída.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: A imagem é dimensionada de modo que se encaixe completamente dentro da área de saída. A taxa de proporção da imagem é preservada.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: A imagem é dimensionada de modo que preencha completamente a área de saída, preservando a proporção original da imagem.  
  
 O exemplo a seguir aplica <xref:System.Windows.Media.Stretch> cada uma <xref:System.Windows.Controls.Image>das enumerações disponíveis a um .  
  
 A imagem a seguir mostra a saída do <xref:System.Windows.Controls.Image.Stretch%2A> exemplo e demonstra o efeito que as diferentes configurações têm quando aplicadas a uma imagem.  
  
 ![Diferentes configurações de alongamento de TileBrush](./media/img-mmgraphics-stretchenum.jpg "img_mmgraphics_stretchenum")  
Configurações diferentes de alongamento  
  
 [!code-xaml[ImageElementExample_snip#ImageStretchExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageStretchExample.xaml#imagestretchexamplewholepage)]  
  
### <a name="painting-with-images"></a>Pintura com imagens  
 As imagens também podem ser exibidas <xref:System.Windows.Media.Brush>em um aplicativo pintando com um . Os pincéis permitem que você pinte objetos [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] com qualquer coisa, desde cores simples e sólidas a conjuntos complexos de padrões e imagens. Para pintar com imagens, use um <xref:System.Windows.Media.ImageBrush>. Um <xref:System.Windows.Media.ImageBrush> é um <xref:System.Windows.Media.TileBrush> tipo de que define seu conteúdo como uma imagem bitmap. Um <xref:System.Windows.Media.ImageBrush> exibe uma única imagem, que <xref:System.Windows.Media.ImageBrush.ImageSource%2A> é especificada por sua propriedade. É possível controlar como a imagem é alongada, alinhada e organizada lado a lado, permitindo que você evite distorção e produza padrões e outros efeitos. A ilustração a seguir mostra alguns efeitos que podem ser alcançados com um <xref:System.Windows.Media.ImageBrush>.  
  
 ![Exemplos de saída de ImageBrush](./media/wcpsdk-mmgraphics-imagebrushexamples.gif "wcpsdk_mmgraphics_imagebrushexamples")  
Os pincéis de imagem podem preencher formas, controles, texto e muito mais  
  
 O exemplo a seguir demonstra como pintar o fundo <xref:System.Windows.Media.ImageBrush>de um botão com uma imagem usando um .  
  
 [!code-xaml[UsingImageBrush#4](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush/CS/PaintingWithImages.xaml#4)]  
  
 Para obter <xref:System.Windows.Media.ImageBrush> informações adicionais sobre e pintar imagens, consulte [Pintura com Imagens, Desenhos e Visuais.](painting-with-images-drawings-and-visuals.md)  
  
<a name="_metadata"></a>
## <a name="image-metadata"></a>Metadados de imagem  
 Alguns arquivos de imagem contêm metadados que descrevem o conteúdo ou as características do arquivo. Por exemplo, a maioria das câmeras digitais criam imagens que contêm metadados sobre a marca e modelo da câmera usada para capturar a imagem. Cada formato de imagem lida com metadados de forma diferente, mas o WPF Imaging fornece uma maneira uniforme de armazenar e recuperar metadados para cada formato de imagem suportado.  
  
 O acesso aos metadados <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A> é fornecido <xref:System.Windows.Media.Imaging.BitmapSource> através da propriedade de um objeto. <xref:System.Windows.Media.Imaging.BitmapSource.Metadata%2A>retorna <xref:System.Windows.Media.Imaging.BitmapMetadata> um objeto que inclui todos os metadados contidos pela imagem. Esses dados podem estar em um esquema de metadados ou em uma combinação de esquemas diferentes. O WPF Imaging suporta os seguintes esquemas de metadados de imagem: Arquivo de imagem exchangeable (Exif), tEXt (PNG Textual Data), diretório de arquivos de imagem (IFD), International Press Telecommunications Council (IPTC) e Extensible Metadata Platform (XMP).  
  
 Para simplificar o processo de leitura <xref:System.Windows.Media.Imaging.BitmapMetadata> de metadados, fornece várias <xref:System.Windows.Media.Imaging.BitmapMetadata.Author%2A>propriedades <xref:System.Windows.Media.Imaging.BitmapMetadata.Title%2A>nomeadas que podem ser facilmente acessadas, tais como , e <xref:System.Windows.Media.Imaging.BitmapMetadata.CameraModel%2A>. Muitas dessas propriedades nomeadas também podem ser usadas para gravar metadados. O suporte adicional para a leitura de metadados é fornecido pelo leitor de consulta de metadados. O <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> método é usado para recuperar um leitor de consulta de metadados, fornecendo uma consulta de strings como *"/app1/exif/"*. No exemplo a <xref:System.Windows.Media.Imaging.BitmapMetadata.GetQuery%2A> seguir, é usado para obter o texto armazenado no local *"/Texto/Descrição".*  
  
 [!code-cpp[BitmapMetadata#GetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#getquery)]
 [!code-csharp[BitmapMetadata#GetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#getquery)]
 [!code-vb[BitmapMetadata#GetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#getquery)]  
  
 Para gravar metadados, usa-se um gravador de consulta de metadados. <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A>obtém o autor da consulta e define o valor desejado. No exemplo a <xref:System.Windows.Media.Imaging.BitmapMetadata.SetQuery%2A> seguir, é usado para escrever o texto armazenado no local *"/Texto/Descrição".*  
  
 [!code-cpp[BitmapMetadata#SetQuery](~/samples/snippets/cpp/VS_Snippets_Wpf/BitMapMetadata/CPP/BitmapMetadata.cpp#setquery)]
 [!code-csharp[BitmapMetadata#SetQuery](~/samples/snippets/csharp/VS_Snippets_Wpf/BitMapMetadata/CSharp/BitmapMetadata.cs#setquery)]
 [!code-vb[BitmapMetadata#SetQuery](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BitMapMetadata/VB/BitmapMetadata.vb#setquery)]  
  
<a name="_extensibility"></a>
## <a name="codec-extensibility"></a>Extensibilidade de codec  
 Uma característica central do WPF Imaging é o modelo de extensibilidade para novos codecs de imagem. Essas interfaces não gerenciadas permitem que os desenvolvedores de codec integrem codecs com o WPF para que novos formatos de imagem possam ser usados automaticamente por aplicativos WPF.  
  
 Para obter uma amostra da API de extensibilidade, consulte o [Código de Amostra Win32](https://go.microsoft.com/fwlink/?LinkID=160052). Este exemplo demonstra como criar um decodificador e codificador para um formato de imagem personalizado.  
  
> [!NOTE]
> O codec deve ser assinado digitalmente para que o sistema o reconheça.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.Imaging.BitmapSource>
- <xref:System.Windows.Media.Imaging.BitmapImage>
- <xref:System.Windows.Controls.Image>
- <xref:System.Windows.Media.Imaging.BitmapMetadata>
- [Elementos gráficos e geração de imagens 2D](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Codec de exemplo do Win32](https://go.microsoft.com/fwlink/?LinkID=160052)
