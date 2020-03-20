---
title: Usando objetos DrawingVisual
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual layer [WPF], DrawingVisual objects
- DrawingVisual objects in visual layer [WPF]
ms.assetid: 0b4e711d-e640-40cb-81c3-8f5c59909b7d
ms.openlocfilehash: 9d67fbc0d9716c9df3935232c6c7e579b50d55bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148316"
---
# <a name="using-drawingvisual-objects"></a>Usando objetos DrawingVisual
Este tópico fornece uma visão <xref:System.Windows.Media.DrawingVisual> geral de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] como usar objetos na camada visual.  
  
<a name="drawingvisual_object"></a>
## <a name="drawingvisual-object"></a>Objeto DrawingVisual  
 A <xref:System.Windows.Media.DrawingVisual> é uma classe de desenho leve que é usada para renderizar formas, imagens ou texto. Essa classe é considerada leve porque não fornece layout ou manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para telas de fundo e clip-art.  
  
<a name="drawingvisual_host_container"></a>
## <a name="drawingvisual-host-container"></a>Contêiner de host do DrawingVisual  
 Para usar <xref:System.Windows.Media.DrawingVisual> objetos, você precisa criar um recipiente de host para os objetos. O objeto do contêiner <xref:System.Windows.FrameworkElement> host deve derivar da classe, que <xref:System.Windows.Media.DrawingVisual> fornece o suporte de layout e manuseio de eventos que a classe não possui. O objeto do contêiner de host não exibe nenhuma propriedade visível, já que sua função principal é conter objetos filho. No entanto, a <xref:System.Windows.UIElement.Visibility%2A> propriedade do <xref:System.Windows.Visibility.Visible>recipiente de hospedagem deve ser definida como; caso contrário, nenhum de seus elementos infantis será visível.  
  
 Quando você cria um objeto de contêiner host para objetos visuais, você precisa armazenar as referências do objeto visual em um <xref:System.Windows.Media.VisualCollection>. Use <xref:System.Windows.Media.VisualCollection.Add%2A> o método para adicionar um objeto visual ao recipiente host. No exemplo a seguir, um objeto de contêiner host é <xref:System.Windows.Media.VisualCollection>criado e três objetos visuais são adicionados ao seu .  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
<a name="creating_drawingvisual_objects"></a>
## <a name="creating-drawingvisual-objects"></a>Criando objetos DrawingVisual  
 Quando você <xref:System.Windows.Media.DrawingVisual> cria um objeto, ele não tem conteúdo de desenho. Você pode adicionar texto, gráficos ou conteúdo de <xref:System.Windows.Media.DrawingContext> imagem recuperando o objeto e puxando para ele. A <xref:System.Windows.Media.DrawingContext> é devolvido chamando <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> o <xref:System.Windows.Media.DrawingVisual> método de um objeto.  
  
 Para desenhar um retângulo <xref:System.Windows.Media.DrawingContext>no <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> , <xref:System.Windows.Media.DrawingContext> use o método do objeto. Existem métodos semelhantes para desenhar outros tipos de conteúdo. Quando terminar de desenhar <xref:System.Windows.Media.DrawingContext>conteúdo no <xref:System.Windows.Media.DrawingContext.Close%2A> , chame <xref:System.Windows.Media.DrawingContext> o método para fechar e persistir o conteúdo.  
  
 No exemplo a <xref:System.Windows.Media.DrawingVisual> seguir, um objeto é criado, e <xref:System.Windows.Media.DrawingContext>um retângulo é atraído para dentro de seu .  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>
## <a name="creating-overrides-for-frameworkelement-members"></a>Criando substituições para membros FrameworkElement  
 O objeto do contêiner de host é responsável por gerenciar sua coleção de objetos visuais. Isso exige que o membro de implemento <xref:System.Windows.FrameworkElement> do contêiner host seja substituido pela classe derivada.  
  
 A lista a seguir descreve os dois membros que você deve substituir:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Devolve uma criança ao índice especificado da coleção de elementos infantis.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtém o número de elementos visuais da criança dentro deste elemento.  
  
 No exemplo a seguir, as <xref:System.Windows.FrameworkElement> substituições para os dois membros são implementadas.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>
## <a name="providing-hit-testing-support"></a>Fornecendo suporte a teste de clique  
 O objeto do contêiner host pode fornecer manipulação de eventos mesmo <xref:System.Windows.UIElement.Visibility%2A> que não <xref:System.Windows.Visibility.Visible>exiba propriedades visíveis — no entanto, sua propriedade deve ser definida como . Isso permite que você crie uma rotina de manipulação de evento para o contêiner de host que pode capturar eventos de mouse, como a liberação do botão esquerdo do mouse. A rotina de manuseio de eventos pode, <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> então, implementar testes de acerto invocando o método. O parâmetro <xref:System.Windows.Media.HitTestResultCallback> do método refere-se a um procedimento definido pelo usuário que você pode usar para determinar a ação resultante de um teste de hit.  
  
 No exemplo a seguir, o suporte para teste de clique é implementado para o objeto do contêiner de host e seus filhos.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
