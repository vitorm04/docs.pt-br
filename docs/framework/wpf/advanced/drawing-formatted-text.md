---
title: Desenhando texto formatado
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 364362e8377f02b5d6518e6ae4d71b6dd1eafc02
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="drawing-formatted-text"></a>Desenhando texto formatado
Este tópico fornece uma visão geral dos recursos do <xref:System.Windows.Media.FormattedText> objeto. Este objeto fornece controle de baixo nível para desenhar texto em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
  
## <a name="technology-overview"></a>Visão geral da tecnologia  
 O <xref:System.Windows.Media.FormattedText> objeto permite que você desenhar texto com várias linha, no qual cada caractere no texto pode ser formatado individualmente. O exemplo a seguir mostra um texto ao qual forma aplicados diversos formatos.  
  
 ![Texto exibido usando o objeto FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Texto exibido usando o método FormattedText  
  
> [!NOTE]
>  Para desenvolvedores que estão migrando da API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], a tabela na seção [Migração do Win32](#win32_migration) lista os sinalizadores DrawText [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e o equivalente aproximado em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Motivos para usar texto formatado  
 O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inclui vários controles para desenhar texto na tela. Cada controle é destinado a um cenário diferente e tem sua própria lista de recursos e limitações. Em geral, o <xref:System.Windows.Controls.TextBlock> elemento deve ser usado ao suporte limitado a texto é necessário, como uma breve frase em um [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>pode ser usado quando é necessário suporte mínimo de texto. Para obter mais informações, consulte [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 O <xref:System.Windows.Media.FormattedText> objeto fornece recursos que de formatação de texto maior [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] controles de texto e pode ser útil em casos em que você deseja usar texto como um elemento decorativo. Para obter mais informações, consulte a seção a seguir [Convertendo texto formatado em uma geometria](#converting_formatted_text).  
  
 Além disso, o <xref:System.Windows.Media.FormattedText> objeto é útil para criar texto <xref:System.Windows.Media.DrawingVisual>-objetos derivados. <xref:System.Windows.Media.DrawingVisual>é uma classe leve que é usada para renderizar formas, imagens ou texto. Para obter mais informações, consulte [Teste de clique usando uma amostra de DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Usando o objeto FormattedText  
 Para criar texto formatado, chame o <xref:System.Windows.Media.FormattedText.%23ctor%2A> construtor para criar um <xref:System.Windows.Media.FormattedText> objeto. Após ter criado a cadeia de caracteres de texto formatado inicial, você poderá aplicar uma variedade de estilos de formatação.  
  
 Use o <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> propriedade para restringir o texto a uma largura específica. O texto será encapsulado automaticamente para evitar que a largura especificada seja ultrapassada. Use o <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> propriedade para restringir o texto a uma altura específica. O texto exibirá reticências, "...", para o texto que ultrapassa a altura especificada.  
  
 ![Texto exibido usando o objeto FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Texto exibido mostrando o encapsulamento de palavras e as reticências  
  
 É possível aplicar vários estilos de formatação a um ou mais caracteres. Por exemplo, você poderia chamar tanto o <xref:System.Windows.Media.FormattedText.SetFontSize%2A> e <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> métodos para alterar a formatação dos cinco primeiros caracteres no texto.  
  
 O exemplo de código a seguir cria um <xref:System.Windows.Media.FormattedText> de objeto e, em seguida, aplica vários estilos de formatação ao texto.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Unidade de medida do tamanho da fonte  
 Assim como acontece com outros objetos de texto em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplicativos, o <xref:System.Windows.Media.FormattedText> objeto usa pixels independentes de dispositivo como a unidade de medida. No entanto, a maioria dos aplicativos [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] usa pontos como unidade de medida. Se quiser usar o texto de exibição em unidades de pontos em aplicativos [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], será necessário converter [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] em pontos. O exemplo de código a seguir mostra como realizar essa conversão.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Convertendo texto formatado em uma geometria  
 Você pode converter texto formatado em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente interessante. Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.  
  
 ![Estrutura de tópicos de texto usando um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Contorno do texto usando um pincel de gradiente linear  
  
 Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais interessantes modificando o traço, o preenchimento e o realce do texto convertido.  
  
 ![Texto com diferentes cores de preenchimento e traço](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Exemplo de configuração de borda e preenchimento com diferentes cores.  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Exemplo de um pincel de imagem aplicado ao traço  
  
 ![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Exemplo de um pincel de imagem aplicado ao traço e ao realce  
  
 Quando o texto é convertido em um <xref:System.Windows.Media.Geometry> do objeto, ele não é mais um conjunto de caracteres — você não pode modificar os caracteres na cadeia de texto. No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento. O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido. Para obter mais informações, consulte [Criar texto contornado](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Você também pode converter texto formatado para um <xref:System.Windows.Media.PathGeometry> de objeto e usar o objeto para realçar o texto. Por exemplo, você pode aplicar uma animação para o <xref:System.Windows.Media.PathGeometry> do objeto para que a animação siga o contorno do texto formatado.  
  
 O exemplo a seguir mostra texto formatado que foi convertido em um <xref:System.Windows.Media.PathGeometry> objeto. Reticências animadas seguem o caminho dos traços do texto renderizado.  
  
 ![Esfera seguindo a geometria do caminho de texto](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Esfera seguindo a geometria de caminho do texto  
  
 Para obter mais informação, consulte [Como criar uma animação de PathGeometry para texto](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Você pode criar outros usos interessantes para texto formatado depois que ele foi convertido em um <xref:System.Windows.Media.PathGeometry> objeto. Por exemplo, você pode recortar um vídeo para exibir dentro dele.  
  
 ![Exibir vídeo no caminho da geometria do texto](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Vídeo em exibição na geometria de caminho do texto  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migração do Win32  
 Os recursos do <xref:System.Windows.Media.FormattedText> para desenho de texto são semelhantes aos recursos do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] função DrawText. Para desenvolvedores que estão migrando da API [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)], a tabela a seguir lista os sinalizadores DrawText [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] e o equivalente aproximado em [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Sinalizador DrawText|Equivalente ao WPF|Observações|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Use o <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para um número apropriado de computação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' posição.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Use o <xref:System.Windows.Media.FormattedText.Height%2A> e <xref:System.Windows.Media.FormattedText.Width%2A> propriedades para calcular o retângulo de saída.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use o <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriedade com o valor definido <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Nenhum|Não obrigatório. A largura do espaço e a renderização da última linha são iguais aos valores no controle de edição da estrutura.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use o <xref:System.Windows.Media.FormattedText.Trimming%2A> propriedade com o valor <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Use <xref:System.Windows.TextTrimming.WordEllipsis> obter [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] finais DT_END_ELLIPSIS com DT_WORD_ELIPSIS — nesse caso, reticências de caractere ocorrem apenas em palavras que não cabem em uma única linha.|  
|DT_EXPAND_TABS|Nenhum|Não obrigatório. As guias são expandidas automaticamente para paradas a cada 4 ems, o que é aproximadamente a largura de 8 caracteres independentes do idioma.|  
|DT_EXTERNALLEADING|Nenhum|Não obrigatório. O entrelinhamento externo sempre é incluído no espaçamento entre linhas. Use o <xref:System.Windows.Media.FormattedText.LineHeight%2A> propriedade para criar espaçamento definido pelo usuário.|  
|DT_HIDEPREFIX|Nenhum|Sem suporte. Remova o '&' da cadeia de caracteres antes de construir o <xref:System.Windows.Media.FormattedText> objeto.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Este é o alinhamento de texto padrão. Use o <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriedade com o valor definido <xref:System.Windows.TextAlignment.Left>. (Somente WPF)|  
|DT_MODIFYSTRING|Nenhum|Sem suporte.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|O recorte não acontece automaticamente. Se você quiser recortar texto, use o <xref:System.Windows.Media.Visual.VisualClip%2A> propriedade.|  
|DT_NOFULLWIDTHCHARBREAK|Nenhum|Sem suporte.|  
|DT_NOPREFIX|Nenhum|Não obrigatório. O caractere "&" nas cadeias de caracteres sempre é tratado como um caractere normal.|  
|DT_PATHELLIPSIS|Nenhum|Use o <xref:System.Windows.Media.FormattedText.Trimming%2A> propriedade com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Nenhum|Sem suporte. Se você deseja usar sublinhados para texto, como uma tecla aceleradora ou link, use o <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> método.|  
|DT_PREFIXONLY|Nenhum|Sem suporte.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Use o <xref:System.Windows.Media.FormattedText.TextAlignment%2A> propriedade com o valor definido <xref:System.Windows.TextAlignment.Right>. (Somente WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Defina a propriedade <xref:System.Windows.Media.FormattedText.FlowDirection%2A> como <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Nenhum|Não obrigatório. <xref:System.Windows.Media.FormattedText>objetos se comportar como um controle de única linha, a menos que o o <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> está definida ou o texto contém uma quebra de linha (CR/LF) de feed.|  
|DT_TABSTOP|Nenhum|Não há suporte para posições de parada de tabulação definidas pelo usuário.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Não obrigatório. A justificação superior é o padrão. Outros valores de posicionamento vertical podem ser definido usando o <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para um número apropriado de computação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' posição.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Use o <xref:System.Windows.Media.FormattedText.Height%2A> propriedade para um número apropriado de computação [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText 'y' posição.|  
|DT_WORDBREAK|Nenhum|Não obrigatório. Linha acontece automaticamente com <xref:System.Windows.Media.FormattedText> objetos. Não é possível desabilitá-la.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Use o <xref:System.Windows.Media.FormattedText.Trimming%2A> propriedade com o valor <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Media.FormattedText>  
 [Documentos no WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Tipografia no WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Criar texto contornado](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Como criar uma animação de PathGeometry para texto](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)
