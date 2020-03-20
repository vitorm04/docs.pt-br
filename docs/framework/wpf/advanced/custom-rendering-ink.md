---
title: Tinta de renderização personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 3cf0d98c40e71a380b218c76d6e52d00cdd05342
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186359"
---
# <a name="custom-rendering-ink"></a>Tinta de renderização personalizada
A <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriedade de um traçado permite especificar a aparência de um traçado, como seu tamanho, cor e <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> forma, mas pode haver momentos em que você deseja personalizar a aparência além do que permite. Convém personalizar a aparência da tinta renderizando na aparência de um pincel de ar, pintura a óleo e muitos outros efeitos. O Windows Presentation Foundation (WPF) permite que você personalize <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke> a renderização de tinta implementando um objeto personalizado.  
  
 Este tópico contém as seguintes subseções:  
  
- [Arquitetura](#Architecture)  
  
- [Implementando um Renderizador Dinâmico](#ImplementingADynamicRenderer)  
  
- [Implementando Traços Personalizados](#ImplementingCustomStrokes)  
  
- [Implementando InkCanvas Personalizado](#ImplementingACustomInkCanvas)  
  
- [Conclusão](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Arquitetura  
 A renderização de tinta ocorre duas vezes; quando um usuário grava tinta em uma superfície de tinta e novamente após o traço ser adicionado à superfície de tinta. A <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderização da tinta quando o usuário move a caneta <xref:System.Windows.Ink.Stroke> do tablet no digitalizador, e a renderização se renderiza uma vez adicionada a um elemento.  
  
 Há três classes para implementar ao renderizar dinamicamente a tinta.  
  
1. **DynamicRenderer**: Implementar uma classe <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>que deriva de . Esta classe é <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> uma especializada que torna o curso como ele é desenhado. A <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renderização em um segmento separado, de modo que a superfície de inking parece coletar tinta mesmo quando o segmento de interface do usuário do aplicativo (UI) está bloqueado. Para obter mais informações sobre o modelo de threading, consulte [O Modelo de Threading de Tinta](the-ink-threading-model.md). Para personalizar a renderização dinâmica <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> de um traçado, anule o método.  
  
2. **Curso**: Implementar uma classe <xref:System.Windows.Ink.Stroke>que deriva de . Esta classe é responsável pela <xref:System.Windows.Input.StylusPoint> renderização estática dos <xref:System.Windows.Ink.Stroke> dados depois de convertido em um objeto. Substituir o <xref:System.Windows.Ink.Stroke.DrawCore%2A> método para garantir que a renderização estática do traçado seja consistente com renderização dinâmica.  
  
3. **InkCanvas:** Implementar uma classe que <xref:System.Windows.Controls.InkCanvas>deriva de . Atribua o <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personalizado <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> à propriedade. Anular o <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> método e adicionar um <xref:System.Windows.Controls.InkCanvas.Strokes%2A> traçado personalizado à propriedade. Isso garante que a aparência da tinta seja consistente.  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>Implementando um Renderizador Dinâmico  
 Embora <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a classe seja [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]uma parte padrão de , para executar renderização mais especializada, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> você deve <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> criar um renderizador dinâmico personalizado que deriva do e substituir o método.  
  
 O exemplo a seguir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> demonstra um personalizado que desenha tinta com um efeito de escova gradiente linear.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>Implementando Traços Personalizados  
 Implementar uma classe que <xref:System.Windows.Ink.Stroke>deriva de . Esta classe é <xref:System.Windows.Input.StylusPoint> responsável pela renderização de <xref:System.Windows.Ink.Stroke> dados depois de convertido em um objeto. Anular a <xref:System.Windows.Ink.Stroke.DrawCore%2A> classe para fazer o desenho real.  
  
 Sua classe Stroke também pode armazenar <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> dados personalizados usando o método. Esses dados são armazenados com os dados de traço quando persistidos.  
  
 A <xref:System.Windows.Ink.Stroke> classe também pode realizar testes de acerto. Você também pode implementar seu próprio algoritmo <xref:System.Windows.Ink.Stroke.HitTest%2A> de teste de acerto substituindo o método na classe atual.  
  
 O código C# a <xref:System.Windows.Ink.Stroke> seguir demonstra <xref:System.Windows.Input.StylusPoint> uma classe personalizada que renderiza os dados como um traçado 3D.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>Implementando InkCanvas Personalizado  
 A maneira mais fácil de <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> usar seu curso personalizado é <xref:System.Windows.Controls.InkCanvas> implementar uma classe que deriva e usa essas classes. O <xref:System.Windows.Controls.InkCanvas> tem <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> uma propriedade que especifica como o traçado é renderizado quando o usuário está desenhando.  
  
 Para personalizar os traçados de renderização em um <xref:System.Windows.Controls.InkCanvas> fazer o seguinte:  
  
- Crie uma classe que <xref:System.Windows.Controls.InkCanvas>deriva do .  
  
- Atribua seu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> personalizado <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> à propriedade.  
  
- Substituir o método <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A>. Nesse método, remova o traço original que foi adicionado ao InkCanvas. Em seguida, crie um traçado personalizado, adicione-o <xref:System.Windows.Controls.InkCanvas.Strokes%2A> à <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> propriedade e chame a classe base com um novo que contenha o traçado personalizado.  
  
 O código C# a <xref:System.Windows.Controls.InkCanvas> seguir demonstra uma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> classe personalizada que usa um personalizado e coleta traçados personalizados.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 Um <xref:System.Windows.Controls.InkCanvas> pode ter <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>mais de um. Você pode <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> adicionar vários <xref:System.Windows.Controls.InkCanvas> objetos ao <xref:System.Windows.UIElement.StylusPlugIns%2A> adicionando-os à propriedade.  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Conclusão  
 Você pode personalizar a aparência da tinta, derivando sua própria <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>e <xref:System.Windows.Controls.InkCanvas> classes. Juntas, essas classes garantem que a aparência do traço seja consistente quando o usuário desenha o traço e após ele ser coletado.  
  
## <a name="see-also"></a>Confira também

- [Tratamento de Tinta Avançado](advanced-ink-handling.md)
