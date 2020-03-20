---
title: Desenhando texto formatado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186559"
---
# <a name="drawing-formatted-text"></a>Desenhando texto formatado
Este tópico fornece uma visão geral <xref:System.Windows.Media.FormattedText> das características do objeto. Este objeto fornece controle de baixo nível para desenhar texto em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Visão geral da tecnologia  
 O <xref:System.Windows.Media.FormattedText> objeto permite desenhar texto multi-linha, no qual cada caractere no texto pode ser formatado individualmente. O exemplo a seguir mostra um texto ao qual forma aplicados diversos formatos.  
  
 ![Texto exibido usando o objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Para aqueles desenvolvedores que migram da API Win32, a tabela na seção [Migração Win32](#win32_migration) [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]lista as bandeiras Win32 DrawText e o equivalente aproximado em .  
  
### <a name="reasons-for-using-formatted-text"></a>Motivos para usar texto formatado  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, <xref:System.Windows.Controls.TextBlock> o elemento deve ser usado quando for necessário suporte [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]de texto limitado, como uma breve frase em um . <xref:System.Windows.Controls.Label>pode ser usado quando o suporte mínimo de texto é necessário. Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
 O <xref:System.Windows.Media.FormattedText> objeto fornece recursos de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] formatação de texto maiores do que controles de texto, e pode ser útil nos casos em que você deseja usar o texto como um elemento decorativo. Para obter mais informações, consulte a seção a seguir [Convertendo texto formatado em uma geometria](#converting_formatted_text).  
  
 Além disso, <xref:System.Windows.Media.FormattedText> o objeto é útil <xref:System.Windows.Media.DrawingVisual>para criar objetos derivados de texto. <xref:System.Windows.Media.DrawingVisual>é uma classe de desenho leve que é usada para renderizar formas, imagens ou texto. Para obter mais informações, consulte [Teste de clique usando uma amostra de DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Usando o objeto FormattedText  
 Para criar texto formatado, chame <xref:System.Windows.Media.FormattedText.%23ctor%2A> o <xref:System.Windows.Media.FormattedText> construtor para criar um objeto. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação.  
  
 Use <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> a propriedade para restringir o texto a uma largura específica. O texto será encapsulado automaticamente para evitar que a largura especificada seja ultrapassada. Use <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> a propriedade para restringir o texto a uma altura específica. O texto exibirá reticências, "...", para o texto que ultrapassa a altura especificada.  
  
 ![Texto exibido com wordwrap e ellipsis.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você pode <xref:System.Windows.Media.FormattedText.SetFontSize%2A> <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> chamar tanto os métodos quanto os métodos para alterar a formatação dos cinco primeiros caracteres no texto.  
  
 O exemplo de <xref:System.Windows.Media.FormattedText> código a seguir cria um objeto e, em seguida, aplica vários estilos de formatação ao texto.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unidade de medida do tamanho da fonte  
 Como acontece com [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] outros objetos <xref:System.Windows.Media.FormattedText> de texto em aplicativos, o objeto usa pixels independentes do dispositivo como unidade de medida. No entanto, a maioria dos aplicativos Win32 usa pontos como unidade de medida. Se você quiser usar texto de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] exibição em unidades de pontos em aplicativos, você precisa converter unidades independentes de dispositivos (1/96polegada por unidade) em pontos. O exemplo de código a seguir mostra como realizar essa conversão.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>Convertendo texto formatado em uma geometria  
 Você pode converter texto <xref:System.Windows.Media.Geometry> formatado em objetos, permitindo criar outros tipos de texto visualmente interessante. Por exemplo, você <xref:System.Windows.Media.Geometry> pode criar um objeto com base no contorno de uma seqüência de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado ao traçado e destaque](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Quando o texto é <xref:System.Windows.Media.Geometry> convertido em um objeto, ele não é mais uma coleção de caracteres — você não pode modificar os caracteres na seqüência de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido. Para obter mais informações, consulte [Criar texto contornado](how-to-create-outlined-text.md).  
  
 Você também pode converter texto <xref:System.Windows.Media.PathGeometry> formatado em um objeto e usar o objeto para destacar o texto. Por exemplo, você pode aplicar <xref:System.Windows.Media.PathGeometry> uma animação ao objeto para que a animação siga o contorno do texto formatado.  
  
 O exemplo a seguir mostra texto formatado <xref:System.Windows.Media.PathGeometry> que foi convertido em um objeto. Reticências animadas seguem o caminho dos traços do texto renderizado.  
  
 ![Esfera seguindo a geometria de caminho do texto](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Esfera seguindo a geometria de caminho do texto  
  
 Para obter mais informação, consulte [Como criar uma animação de PathGeometry para texto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Você pode criar outros usos interessantes para texto <xref:System.Windows.Media.PathGeometry> formatado uma vez que ele tenha sido convertido em um objeto. Por exemplo, você pode recortar um vídeo para exibir dentro dele.  
  
 ![Vídeo em exibição na geometria de caminho do texto](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Migração do Win32  
 As características <xref:System.Windows.Media.FormattedText> do texto para desenho são semelhantes às características da função DrawText do Win32. Para aqueles desenvolvedores que migram da API Win32, a tabela a seguir lista [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]as bandeiras Win32 DrawText e o equivalente aproximado em .  
  
|Sinalizador DrawText|Equivalente ao WPF|Observações|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Use <xref:System.Windows.Media.FormattedText.Height%2A> a propriedade para calcular uma posição 'y' do Win32 DrawText 'y' apropriada.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Use <xref:System.Windows.Media.FormattedText.Height%2A> as <xref:System.Windows.Media.FormattedText.Width%2A> propriedades e para calcular o retângulo de saída.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use <xref:System.Windows.Media.FormattedText.TextAlignment%2A> a propriedade com <xref:System.Windows.TextAlignment.Center>o valor definido para .|  
|DT_EDITCONTROL|Nenhum|Não obrigatório. A largura do espaço e a renderização da última linha são iguais aos valores no controle de edição da estrutura.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use <xref:System.Windows.Media.FormattedText.Trimming%2A> a propriedade <xref:System.Windows.TextTrimming.CharacterEllipsis>com o valor.<br /><br /> Use <xref:System.Windows.TextTrimming.WordEllipsis> para obter o DT_END_ELLIPSIS do Win32 com DT_WORD_ELIPSIS elipse final — neste caso, a elipse de caracteres só ocorre em palavras que não se encaixam em uma única linha.|  
|DT_EXPAND_TABS|Nenhum|Não obrigatório. As guias são expandidas automaticamente para paradas a cada 4 ems, o que é aproximadamente a largura de 8 caracteres independentes do idioma.|  
|DT_EXTERNALLEADING|Nenhum|Não obrigatório. O entrelinhamento externo sempre é incluído no espaçamento entre linhas. Use <xref:System.Windows.Media.FormattedText.LineHeight%2A> a propriedade para criar espaçamento de linha definido pelo usuário.|  
|DT_HIDEPREFIX|Nenhum|Sem suporte. Remova o '&' da string <xref:System.Windows.Media.FormattedText> antes de construir o objeto.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Este é o alinhamento de texto padrão. Use <xref:System.Windows.Media.FormattedText.TextAlignment%2A> a propriedade com <xref:System.Windows.TextAlignment.Left>o valor definido para . (Somente WPF)|  
|DT_MODIFYSTRING|Nenhum|Sem suporte.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|O recorte não acontece automaticamente. Se você quiser cortar texto, use a <xref:System.Windows.Media.Visual.VisualClip%2A> propriedade.|  
|DT_NOFULLWIDTHCHARBREAK|Nenhum|Sem suporte.|  
|DT_NOPREFIX|Nenhum|Não obrigatório. O caractere "&" nas cadeias de caracteres sempre é tratado como um caractere normal.|  
|DT_PATHELLIPSIS|Nenhum|Use <xref:System.Windows.Media.FormattedText.Trimming%2A> a propriedade <xref:System.Windows.TextTrimming.WordEllipsis>com o valor.|  
|DT_PREFIX|Nenhum|Sem suporte. Se você quiser usar sublinhados para texto, como uma <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> chave de acelerador ou link, use o método.|  
|DT_PREFIXONLY|Nenhum|Sem suporte.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use <xref:System.Windows.Media.FormattedText.TextAlignment%2A> a propriedade com <xref:System.Windows.TextAlignment.Right>o valor definido para . (Somente WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Defina a propriedade <xref:System.Windows.Media.FormattedText.FlowDirection%2A> como <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Nenhum|Não obrigatório. <xref:System.Windows.Media.FormattedText>os objetos se comportam como <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> um controle de linha única, a menos que a propriedade esteja definida ou o texto contenha uma alimentação de retorno/linha de transporte (CR/LF).|  
|DT_TABSTOP|Nenhum|Não há suporte para posições de parada de tabulação definidas pelo usuário.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Não obrigatório. A justificação superior é o padrão. Outros valores de posicionamento vertical <xref:System.Windows.Media.FormattedText.Height%2A> podem ser definidos usando a propriedade para calcular uma posição 'y' do Win32 DrawText 'y' apropriada.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Use <xref:System.Windows.Media.FormattedText.Height%2A> a propriedade para calcular uma posição 'y' do Win32 DrawText 'y' apropriada.|  
|DT_WORDBREAK|Nenhum|Não obrigatório. A quebra de <xref:System.Windows.Media.FormattedText> palavras acontece automaticamente com objetos. Não é possível desabilitá-la.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use <xref:System.Windows.Media.FormattedText.Trimming%2A> a propriedade <xref:System.Windows.TextTrimming.WordEllipsis>com o valor.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.FormattedText>
- [Documentos no WPF](documents-in-wpf.md)
- [Tipografia no WPF](typography-in-wpf.md)
- [Criar texto contornado](how-to-create-outlined-text.md)
- [Como criar uma animação de PathGeometry para texto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
