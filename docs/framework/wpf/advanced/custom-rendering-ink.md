---
title: "Tinta de renderização personalizada"
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
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 481990acdf2f5b8f798144d36434569b9e2cd481
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-rendering-ink"></a>Tinta de renderização personalizada
O <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriedade de um traço permite que você especificar a aparência de um traço, como seu tamanho, cor e forma, mas pode haver ocasiões em que você deseja personalizar a aparência além do que <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> permitir. Convém personalizar a aparência da tinta renderizando na aparência de um pincel de ar, pintura a óleo e muitos outros efeitos. O [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] permite renderização personalizada de tinta implementando um personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> e <xref:System.Windows.Ink.Stroke> objeto.  
  
 Este tópico contém as seguintes subseções:  
  
-   [Arquitetura](#Architecture)  
  
-   [Implementando um Renderizador Dinâmico](#ImplementingADynamicRenderer)  
  
-   [Implementando Traços Personalizados](#ImplementingCustomStrokes)  
  
-   [Implementando InkCanvas Personalizado](#ImplementingACustomInkCanvas)  
  
-   [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Arquitetura  
 A renderização de tinta ocorre duas vezes; quando um usuário grava tinta em uma superfície de tinta e novamente após o traço ser adicionado à superfície de tinta. O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderiza a tinta quando o usuário move a caneta no digitalizador e o <xref:System.Windows.Ink.Stroke> renderiza a próprio assim que ele é adicionado a um elemento.  
  
 Há três classes para implementar ao renderizar dinamicamente a tinta.  
  
1.  **DynamicRenderer**: implementar uma classe que deriva de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Essa classe é uma <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> que processa o traço conforme ele é desenhado. O <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> faz a renderização em um thread separado, para a superfície de tinta pareça coletar tinta mesmo quando o thread de interface do usuário de usuário de aplicativo está bloqueado. Para obter mais informações sobre o modelo de threading, consulte [O Modelo de Threading de Tinta](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md). Para personalizar a renderização dinâmica de um traço, substitua o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> método.  
  
2.  **Traço**: implementar uma classe que deriva de <xref:System.Windows.Ink.Stroke>. Essa classe é responsável pela renderização estática do <xref:System.Windows.Input.StylusPoint> dados após ele ter sido convertido em um <xref:System.Windows.Ink.Stroke> objeto. Substituir o <xref:System.Windows.Ink.Stroke.DrawCore%2A> método para garantir que renderização estática do traço é consistente com a renderização dinâmica.  
  
3.  **InkCanvas:** implementar uma classe que deriva de <xref:System.Windows.Controls.InkCanvas>. Atribuir o personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> para o <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriedade. Substituir o <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> método e adicionar um traço personalizado para o <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedade. Isso garante que a aparência da tinta seja consistente.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implementando um Renderizador Dinâmico  
 Embora o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> classe é uma parte padrão de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]executar mais especializadas de renderização, você deve criar um dynamic renderer personalizado que deriva o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> e substituir o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> método.  
  
 O exemplo a seguir demonstra um personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> que desenha tinta com um efeito de pincel de gradiente linear.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implementando Traços Personalizados  
 Implementar uma classe que deriva de <xref:System.Windows.Ink.Stroke>. Essa classe é responsável pela renderização <xref:System.Windows.Input.StylusPoint> dados após ele ter sido convertido em um <xref:System.Windows.Ink.Stroke> objeto. Substituir o <xref:System.Windows.Ink.Stroke.DrawCore%2A> classe para fazer o desenho real.  
  
 A classe Stroke também pode armazenar dados personalizados usando o <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> método. Esses dados são armazenados com os dados de traço quando persistidos.  
  
 O <xref:System.Windows.Ink.Stroke> classe também pode executar teste de clique. Você também pode implementar seu próprio algoritmo por meio da substituição de teste de clique a <xref:System.Windows.Ink.Stroke.HitTest%2A> método na classe atual.  
  
 O código c# a seguir demonstra um personalizado <xref:System.Windows.Ink.Stroke> classe renderiza <xref:System.Windows.Input.StylusPoint> dados como um traço 3-d.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implementando InkCanvas Personalizado  
 A maneira mais fácil de usar seu personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> e traço é implementar uma classe que deriva de <xref:System.Windows.Controls.InkCanvas> e usa essas classes. O <xref:System.Windows.Controls.InkCanvas> tem um <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> propriedade que especifica como o traço é renderizado quando o usuário está desenhando.  
  
 Para personalizar traços são renderizados em um <xref:System.Windows.Controls.InkCanvas> faça o seguinte:  
  
-   Criar uma classe que deriva de <xref:System.Windows.Controls.InkCanvas>.  
  
-   Atribuir o personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> para o <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> propriedade.  
  
-   Substituir o método <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>. Nesse método, remova o traço original que foi adicionado ao InkCanvas. Em seguida, crie um traço personalizado, adicione-o para o <xref:System.Windows.Controls.InkCanvas.Strokes%2A> propriedade e chame a classe base com um novo <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> que contém o traço personalizado.  
  
 O código c# a seguir demonstra um personalizado <xref:System.Windows.Controls.InkCanvas> classe que usa um personalizado <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> e coleta traços personalizados.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Um <xref:System.Windows.Controls.InkCanvas> pode ter mais de um <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Você pode adicionar várias <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objetos para o <xref:System.Windows.Controls.InkCanvas> adicionando-as para o <xref:System.Windows.UIElement.StylusPlugIns%2A> propriedade.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Conclusão  
 Você pode personalizar a aparência de tinta criando suas próprias <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, e <xref:System.Windows.Controls.InkCanvas> classes. Juntas, essas classes garantem que a aparência do traço seja consistente quando o usuário desenha o traço e após ele ser coletado.  
  
## <a name="see-also"></a>Consulte também  
 [Tratamento de Tinta Avançado](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
