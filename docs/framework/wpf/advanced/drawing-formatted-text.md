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
ms.openlocfilehash: 3b410bcf609aca2cb201042247b8768f243ac93a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629748"
---
# <a name="drawing-formatted-text"></a>Desenhando texto formatado
Este tópico fornece uma visão geral dos recursos do <xref:System.Windows.Media.FormattedText> objeto. Este objeto fornece controle de baixo nível para desenhar texto em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Visão geral da tecnologia  
 O <xref:System.Windows.Media.FormattedText> objeto permite desenhar texto de várias linhas, no qual cada caractere no texto pode ser formatado individualmente. O exemplo a seguir mostra um texto ao qual forma aplicados diversos formatos.  
  
 ![Texto exibido usando o objeto FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
>  Para desenvolvedores que estão migrando da API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], a tabela na seção [Migração do Win32](#win32_migration) lista os sinalizadores DrawText [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e o equivalente aproximado em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Motivos para usar texto formatado  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, o <xref:System.Windows.Controls.TextBlock> elemento deve ser usado quando o suporte a texto limitado é necessário, como uma breve frase em [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]um. <xref:System.Windows.Controls.Label>pode ser usado quando o suporte a texto mínimo é necessário. Para obter mais informações, consulte [Documentos no WPF](documents-in-wpf.md).  
  
 O <xref:System.Windows.Media.FormattedText> objeto fornece mais recursos de formatação de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] texto que controles de texto e pode ser útil em casos em que você deseja usar texto como um elemento decorativo. Para obter mais informações, consulte a seção a seguir [Convertendo texto formatado em uma geometria](#converting_formatted_text).  
  
 Além disso, o <xref:System.Windows.Media.FormattedText> objeto é útil para criar objetos derivados de <xref:System.Windows.Media.DrawingVisual>texto. <xref:System.Windows.Media.DrawingVisual>é uma classe de desenho leve que é usada para renderizar formas, imagens ou texto. Para obter mais informações, consulte [Teste de clique usando uma amostra de DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Usando o objeto FormattedText  
 Para criar texto formatado, chame o <xref:System.Windows.Media.FormattedText.%23ctor%2A> Construtor para criar um <xref:System.Windows.Media.FormattedText> objeto. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação.  
  
 Use a <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> propriedade para restringir o texto a uma largura específica. O texto será encapsulado automaticamente para evitar que a largura especificada seja ultrapassada. Use a <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> propriedade para restringir o texto a uma altura específica. O texto exibirá reticências, "...", para o texto que ultrapassa a altura especificada.  
  
 ![Texto exibido com WordWrap e reticências.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você poderia chamar ambos os <xref:System.Windows.Media.FormattedText.SetFontSize%2A> métodos <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> e para alterar a formatação dos cinco primeiros caracteres no texto.  
  
 O exemplo de código a seguir <xref:System.Windows.Media.FormattedText> cria um objeto e, em seguida, aplica vários estilos de formatação ao texto.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unidade de medida do tamanho da fonte  
 Assim como ocorre com outros objetos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] de texto em <xref:System.Windows.Media.FormattedText> aplicativos, o objeto usa pixels independentes de dispositivo como a unidade de medida. No entanto, a maioria dos aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] usa pontos como unidade de medida. Se você quiser usar o texto de exibição em unidades de pontos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] em aplicativos, precisará converter unidades independentes de dispositivo (1/1/96 polegada por unidade) em pontos. O exemplo de código a seguir mostra como realizar essa conversão.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Convertendo texto formatado em uma geometria  
 Você pode converter texto formatado em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente interessante. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de texto.  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com cores diferentes para preenchimento e traço](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Texto com pincel de imagem aplicado a Stroke e realce](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Quando o texto é convertido em <xref:System.Windows.Media.Geometry> um objeto, ele não é mais uma coleção de caracteres — não é possível modificar os caracteres na cadeia de caracteres de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido. Para obter mais informações, consulte [Criar texto contornado](how-to-create-outlined-text.md).  
  
 Você também pode converter o texto formatado em <xref:System.Windows.Media.PathGeometry> um objeto e usar o objeto para realçar o texto. Por exemplo, você pode aplicar uma animação ao <xref:System.Windows.Media.PathGeometry> objeto para que a animação siga o contorno do texto formatado.  
  
 O exemplo a seguir mostra o texto formatado que foi convertido em <xref:System.Windows.Media.PathGeometry> um objeto. Reticências animadas seguem o caminho dos traços do texto renderizado.  
  
 ![Esfera seguindo a geometria de caminho do texto](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Esfera seguindo a geometria de caminho do texto  
  
 Para obter mais informações, confira [Como: Crie uma animação de PathGeometry para](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))texto.  
  
 Você pode criar outros usos interessantes para texto formatado depois que ele tiver sido convertido em <xref:System.Windows.Media.PathGeometry> um objeto. Por exemplo, você pode recortar um vídeo para exibir dentro dele.  
  
 ![Vídeo em exibição na geometria de caminho do texto](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migração do Win32  
 Os recursos do <xref:System.Windows.Media.FormattedText> para o [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] texto de desenho são semelhantes aos recursos da função DrawText. Para desenvolvedores que estão migrando da API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], a tabela a seguir lista os sinalizadores DrawText [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e o equivalente aproximado em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Sinalizador DrawText|Equivalente ao WPF|Observações|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Use a <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para calcular uma posição [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ' y ' apropriada do DrawText.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Use as <xref:System.Windows.Media.FormattedText.Height%2A> propriedades <xref:System.Windows.Media.FormattedText.Width%2A> e para calcular o retângulo de saída.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use a <xref:System.Windows.Media.FormattedText.TextAlignment%2A> Propriedade com o valor definido como <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Nenhum|Não obrigatório. A largura do espaço e a renderização da última linha são iguais aos valores no controle de edição da estrutura.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use a <xref:System.Windows.Media.FormattedText.Trimming%2A> Propriedade com o valor <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Use <xref:System.Windows.TextTrimming.WordEllipsis> para obter [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS com reticências de extremidade DT_WORD_ELIPSIS – nesse caso, reticências de caractere só ocorrem em palavras que não se ajustam em uma única linha.|  
|DT_EXPAND_TABS|Nenhum|Não obrigatório. As guias são expandidas automaticamente para paradas a cada 4 ems, o que é aproximadamente a largura de 8 caracteres independentes do idioma.|  
|DT_EXTERNALLEADING|Nenhum|Não obrigatório. O entrelinhamento externo sempre é incluído no espaçamento entre linhas. Use a <xref:System.Windows.Media.FormattedText.LineHeight%2A> propriedade para criar um espaçamento de linha definido pelo usuário.|  
|DT_HIDEPREFIX|Nenhum|Sem suporte. Remova o ' & ' da cadeia de caracteres antes de construir <xref:System.Windows.Media.FormattedText> o objeto.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Este é o alinhamento de texto padrão. Use a <xref:System.Windows.Media.FormattedText.TextAlignment%2A> Propriedade com o valor definido como <xref:System.Windows.TextAlignment.Left>. (Somente WPF)|  
|DT_MODIFYSTRING|Nenhum|Sem suporte.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|O recorte não acontece automaticamente. Se você quiser recortar o texto, use <xref:System.Windows.Media.Visual.VisualClip%2A> a propriedade.|  
|DT_NOFULLWIDTHCHARBREAK|Nenhum|Sem suporte.|  
|DT_NOPREFIX|Nenhum|Não obrigatório. O caractere "&" nas cadeias de caracteres sempre é tratado como um caractere normal.|  
|DT_PATHELLIPSIS|Nenhum|Use a <xref:System.Windows.Media.FormattedText.Trimming%2A> Propriedade com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Nenhum|Sem suporte. Se você quiser usar sublinhados para texto, como uma tecla aceleradora ou link, use o <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> método.|  
|DT_PREFIXONLY|Nenhum|Sem suporte.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use a <xref:System.Windows.Media.FormattedText.TextAlignment%2A> Propriedade com o valor definido como <xref:System.Windows.TextAlignment.Right>. (Somente WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Defina a propriedade <xref:System.Windows.Media.FormattedText.FlowDirection%2A> como <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Nenhum|Não obrigatório. <xref:System.Windows.Media.FormattedText>os objetos se comportam como um controle de linha <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> única, a menos que a propriedade seja definida ou o texto contenha uma CR/LF (retorno de carro/alimentação de linha).|  
|DT_TABSTOP|Nenhum|Não há suporte para posições de parada de tabulação definidas pelo usuário.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Não obrigatório. A justificação superior é o padrão. Outros valores de posicionamento vertical podem ser definidos usando a <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para calcular uma posição [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ' y ' apropriada do DrawText.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Use a <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para calcular uma posição [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] ' y ' apropriada do DrawText.|  
|DT_WORDBREAK|Nenhum|Não obrigatório. A quebra de palavras ocorre <xref:System.Windows.Media.FormattedText> automaticamente com objetos. Não é possível desabilitá-la.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use a <xref:System.Windows.Media.FormattedText.Trimming%2A> Propriedade com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.FormattedText>
- [Documentos no WPF](documents-in-wpf.md)
- [Tipografia no WPF](typography-in-wpf.md)
- [Criar texto contornado](how-to-create-outlined-text.md)
- [Como: Criar uma animação de PathGeometry para texto](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
