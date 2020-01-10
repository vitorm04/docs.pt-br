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
ms.openlocfilehash: c786137a471e0199a8ac60f8d82b4ce440e33b7e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740404"
---
# <a name="drawing-formatted-text"></a>Desenhando texto formatado
Este tópico fornece uma visão geral dos recursos do objeto <xref:System.Windows.Media.FormattedText>. Este objeto fornece controle de baixo nível para desenhar texto em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Visão geral da tecnologia  
 O objeto <xref:System.Windows.Media.FormattedText> permite desenhar texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. O exemplo a seguir mostra um texto ao qual forma aplicados diversos formatos.  
  
 ![Texto exibido usando o objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Para os desenvolvedores que estão migrando da API do Win32, a tabela na seção de [migração do Win32](#win32_migration) lista os sinalizadores de DrawText do Win32 e o equivalente aproximado em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Motivos para usar texto formatado  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, o elemento <xref:System.Windows.Controls.TextBlock> deve ser usado quando o suporte a texto limitado é necessário, como uma breve frase em uma [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> pode ser usado quando o suporte a texto mínimo é necessário. Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
 O objeto <xref:System.Windows.Media.FormattedText> fornece mais recursos de formatação de texto do que [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controles de texto e pode ser útil em casos em que você deseja usar texto como um elemento decorativo. Para obter mais informações, consulte a seção a seguir [Convertendo texto formatado em uma geometria](#converting_formatted_text).  
  
 Além disso, o objeto <xref:System.Windows.Media.FormattedText> é útil para criar objetos derivados de texto <xref:System.Windows.Media.DrawingVisual>. <xref:System.Windows.Media.DrawingVisual> é uma classe leve de desenho que é usada para renderizar formas, imagens ou texto. Para obter mais informações, consulte [Teste de clique usando uma amostra de DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Usando o objeto FormattedText  
 Para criar texto formatado, chame o Construtor <xref:System.Windows.Media.FormattedText.%23ctor%2A> para criar um objeto <xref:System.Windows.Media.FormattedText>. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação.  
  
 Use a propriedade <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> para restringir o texto a uma largura específica. O texto será encapsulado automaticamente para evitar que a largura especificada seja ultrapassada. Use a propriedade <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> para restringir o texto a uma altura específica. O texto exibirá reticências, "...", para o texto que ultrapassa a altura especificada.  
  
 ![Texto exibido com WordWrap e reticências.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você pode chamar os métodos <xref:System.Windows.Media.FormattedText.SetFontSize%2A> e <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> para alterar a formatação dos cinco primeiros caracteres no texto.  
  
 O exemplo de código a seguir cria um objeto <xref:System.Windows.Media.FormattedText> e, em seguida, aplica vários estilos de formatação ao texto.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unidade de medida do tamanho da fonte  
 Assim como ocorre com outros objetos de texto em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], o objeto <xref:System.Windows.Media.FormattedText> usa pixels independentes de dispositivo como a unidade de medida. No entanto, a maioria dos aplicativos Win32 usa pontos como a unidade de medida. Se desejar usar o texto de exibição em unidades de pontos em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você precisará converter unidades independentes de dispositivo (1/1/96 polegada por unidade) em pontos. O exemplo de código a seguir mostra como realizar essa conversão.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Convertendo texto formatado em uma geometria  
 Você pode converter texto formatado em objetos <xref:System.Windows.Media.Geometry>, permitindo que você crie outros tipos de texto visualmente interessante. Por exemplo, você pode criar um objeto <xref:System.Windows.Media.Geometry> com base no contorno de uma cadeia de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com cores diferentes para preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado a Stroke e realce](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Quando o texto é convertido em um objeto <xref:System.Windows.Media.Geometry>, ele não é mais uma coleção de caracteres — não é possível modificar os caracteres na cadeia de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido. Para obter mais informações, consulte [Criar texto contornado](how-to-create-outlined-text.md).  
  
 Você também pode converter texto formatado em um objeto <xref:System.Windows.Media.PathGeometry> e usar o objeto para realçar o texto. Por exemplo, você pode aplicar uma animação ao objeto <xref:System.Windows.Media.PathGeometry> para que a animação siga o contorno do texto formatado.  
  
 O exemplo a seguir mostra o texto formatado que foi convertido em um objeto <xref:System.Windows.Media.PathGeometry>. Reticências animadas seguem o caminho dos traços do texto renderizado.  
  
 ![Esfera seguindo a geometria de caminho do texto](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Esfera seguindo a geometria de caminho do texto  
  
 Para obter mais informação, consulte [Como criar uma animação de PathGeometry para texto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Você pode criar outros usos interessantes para texto formatado depois que ele tiver sido convertido em um objeto <xref:System.Windows.Media.PathGeometry>. Por exemplo, você pode recortar um vídeo para exibir dentro dele.  
  
 ![Vídeo em exibição na geometria de caminho do texto](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migração do Win32  
 Os recursos de <xref:System.Windows.Media.FormattedText> para o texto de desenho são semelhantes aos recursos da função DrawText do Win32. Para os desenvolvedores que estão migrando da API do Win32, a tabela a seguir lista os sinalizadores de DrawText do Win32 e o equivalente aproximado no [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Sinalizador DrawText|Equivalente ao WPF|{1&gt;Observações&lt;1}|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.Height%2A> para calcular uma posição ' y ' apropriada do DrawText do Win32.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Use as propriedades <xref:System.Windows.Media.FormattedText.Height%2A> e <xref:System.Windows.Media.FormattedText.Width%2A> para calcular o retângulo de saída.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.TextAlignment%2A> com o valor definido como <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|{1&gt;Nenhum&lt;1}|Não obrigatório. A largura do espaço e a renderização da última linha são iguais aos valores no controle de edição da estrutura.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.Trimming%2A> com o valor <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Use <xref:System.Windows.TextTrimming.WordEllipsis> para obter DT_END_ELLIPSIS do Win32 com DT_WORD_ELIPSIS reticências de término — nesse caso, reticências de caractere só ocorrem em palavras que não se ajustam em uma única linha.|  
|DT_EXPAND_TABS|{1&gt;Nenhum&lt;1}|Não obrigatório. As guias são expandidas automaticamente para paradas a cada 4 ems, o que é aproximadamente a largura de 8 caracteres independentes do idioma.|  
|DT_EXTERNALLEADING|{1&gt;Nenhum&lt;1}|Não obrigatório. O entrelinhamento externo sempre é incluído no espaçamento entre linhas. Use a propriedade <xref:System.Windows.Media.FormattedText.LineHeight%2A> para criar espaçamento de linha definido pelo usuário.|  
|DT_HIDEPREFIX|{1&gt;Nenhum&lt;1}|{1&gt;Sem suporte.&lt;1} Remova o ' & ' da cadeia de caracteres antes de construir o objeto <xref:System.Windows.Media.FormattedText>.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Este é o alinhamento de texto padrão. Use a propriedade <xref:System.Windows.Media.FormattedText.TextAlignment%2A> com o valor definido como <xref:System.Windows.TextAlignment.Left>. (Somente WPF)|  
|DT_MODIFYSTRING|{1&gt;Nenhum&lt;1}|{1&gt;Sem suporte.&lt;1}|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|O recorte não acontece automaticamente. Se você quiser recortar o texto, use a propriedade <xref:System.Windows.Media.Visual.VisualClip%2A>.|  
|DT_NOFULLWIDTHCHARBREAK|{1&gt;Nenhum&lt;1}|{1&gt;Sem suporte.&lt;1}|  
|DT_NOPREFIX|{1&gt;Nenhum&lt;1}|Não obrigatório. O caractere "&" nas cadeias de caracteres sempre é tratado como um caractere normal.|  
|DT_PATHELLIPSIS|{1&gt;Nenhum&lt;1}|Use a propriedade <xref:System.Windows.Media.FormattedText.Trimming%2A> com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|{1&gt;Nenhum&lt;1}|{1&gt;Sem suporte.&lt;1} Se você quiser usar sublinhados para texto, como uma tecla aceleradora ou link, use o método <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>.|  
|DT_PREFIXONLY|{1&gt;Nenhum&lt;1}|{1&gt;Sem suporte.&lt;1}|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.TextAlignment%2A> com o valor definido como <xref:System.Windows.TextAlignment.Right>. (Somente WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Defina a propriedade <xref:System.Windows.Media.FormattedText.FlowDirection%2A> como <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|{1&gt;Nenhum&lt;1}|Não obrigatório. <xref:System.Windows.Media.FormattedText> objetos se comportam como um controle de linha única, a menos que a propriedade <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> seja definida ou o texto contenha uma CR/LF (retorno de carro/alimentação de linha).|  
|DT_TABSTOP|{1&gt;Nenhum&lt;1}|Não há suporte para posições de parada de tabulação definidas pelo usuário.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Não obrigatório. A justificação superior é o padrão. Outros valores de posicionamento vertical podem ser definidos usando a propriedade <xref:System.Windows.Media.FormattedText.Height%2A> para calcular uma posição ' y ' apropriada do DrawText do Win32.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.Height%2A> para calcular uma posição ' y ' apropriada do DrawText do Win32.|  
|DT_WORDBREAK|{1&gt;Nenhum&lt;1}|Não obrigatório. A quebra de palavras ocorre automaticamente com <xref:System.Windows.Media.FormattedText> objetos. Não é possível desabilitá-la.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use a propriedade <xref:System.Windows.Media.FormattedText.Trimming%2A> com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Veja também

- <xref:System.Windows.Media.FormattedText>
- [Documentos no WPF](documents-in-wpf.md)
- [Tipografia no WPF](typography-in-wpf.md)
- [Criar texto contornado](how-to-create-outlined-text.md)
- [Como criar uma animação de PathGeometry para texto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
