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
ms.openlocfilehash: 4e6fc89b64f7b0acc1a0077708d567eb97e2868e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962837"
---
# <a name="using-drawingvisual-objects"></a>Usando objetos DrawingVisual
Este tópico fornece uma visão geral de como usar <xref:System.Windows.Media.DrawingVisual> objetos [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na camada Visual.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objeto DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> é uma classe leve de desenho que é usada para renderizar formas, imagens ou texto. Essa classe é considerada leve porque não fornece layout nem manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para planos de fundo e clip-art.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Contêiner de host do DrawingVisual  
 Para usar <xref:System.Windows.Media.DrawingVisual> objetos, você precisa criar um contêiner de host para os objetos. O objeto contêiner host deve derivar da <xref:System.Windows.FrameworkElement> classe, que fornece o suporte ao layout e ao tratamento de <xref:System.Windows.Media.DrawingVisual> eventos que a classe não tem. O objeto do contêiner de host não exibe nenhuma propriedade visível, já que sua função principal é conter objetos filho. No entanto <xref:System.Windows.UIElement.Visibility%2A> , a propriedade do contêiner host deve ser definida <xref:System.Windows.Visibility.Visible>como; caso contrário, nenhum de seus elementos filho será visível.  
  
 Ao criar um objeto de contêiner de host para objetos visuais, você precisa armazenar as referências de objeto visual em <xref:System.Windows.Media.VisualCollection>um. Use o <xref:System.Windows.Media.VisualCollection.Add%2A> método para adicionar um objeto visual ao contêiner de host. No exemplo a seguir, um objeto de contêiner de host é criado e três objetos visuais são adicionados ao <xref:System.Windows.Media.VisualCollection>seu.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
> Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Criando objetos DrawingVisual  
 Quando você cria um <xref:System.Windows.Media.DrawingVisual> objeto, ele não tem nenhum conteúdo de desenho. Você pode adicionar conteúdo de texto, gráficos ou imagens recuperando o objeto <xref:System.Windows.Media.DrawingContext> e o desenho nele. Um <xref:System.Windows.Media.DrawingContext> é retornado chamando o <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> método de um <xref:System.Windows.Media.DrawingVisual> objeto.  
  
 Para desenhar um retângulo no <xref:System.Windows.Media.DrawingContext>, use o <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> método do <xref:System.Windows.Media.DrawingContext> objeto. Existem métodos semelhantes para desenhar outros tipos de conteúdo. Quando você terminar de desenhar o conteúdo no <xref:System.Windows.Media.DrawingContext>, chame o <xref:System.Windows.Media.DrawingContext.Close%2A> método para fechar o <xref:System.Windows.Media.DrawingContext> e persistir o conteúdo.  
  
 No exemplo a seguir, um <xref:System.Windows.Media.DrawingVisual> objeto é criado e um retângulo é desenhado em seu. <xref:System.Windows.Media.DrawingContext>  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Criando substituições para membros FrameworkElement  
 O objeto do contêiner de host é responsável por gerenciar sua coleção de objetos visuais. Isso requer que o contêiner de host implemente substituições de <xref:System.Windows.FrameworkElement> membro para a classe derivada.  
  
 A lista a seguir descreve os dois membros que você deve substituir:  
  
- <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Retorna um filho no índice especificado da coleção de elementos filho.  
  
- <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtém o número de elementos filho visuais dentro desse elemento.  
  
 No exemplo a seguir, as substituições para <xref:System.Windows.FrameworkElement> os dois membros são implementadas.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Fornecendo suporte a teste de clique  
 O objeto de contêiner host pode fornecer manipulação de eventos, mesmo se não exibir nenhuma propriedade visível — no entanto, sua <xref:System.Windows.UIElement.Visibility%2A> Property deve ser definida como. <xref:System.Windows.Visibility.Visible> Isso permite que você crie uma rotina de manipulação de evento para o contêiner de host que pode capturar eventos de mouse, como a liberação do botão esquerdo do mouse. A rotina de manipulação de eventos pode implementar o teste de clique invocando o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método. O parâmetro do <xref:System.Windows.Media.HitTestResultCallback> método refere-se a um procedimento definido pelo usuário que você pode usar para determinar a ação resultante de um teste de clique.  
  
 No exemplo a seguir, o suporte para teste de clique é implementado para o objeto do contêiner de host e seus filhos.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
