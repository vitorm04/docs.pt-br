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
ms.openlocfilehash: 01e10a4b0f0bf4959850caf3951ad4ea915edb4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59121713"
---
# <a name="using-drawingvisual-objects"></a>Usando objetos DrawingVisual
Este tópico fornece uma visão geral de como usar <xref:System.Windows.Media.DrawingVisual> objetos no [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] camada visual.  
  
<a name="drawingvisual_object"></a>   
## <a name="drawingvisual-object"></a>Objeto DrawingVisual  
 O <xref:System.Windows.Media.DrawingVisual> é uma classe que é usada para renderizar formas, imagens ou texto leve. Essa classe é considerada leve porque não fornece layout nem manipulação de eventos, o que melhora o desempenho. Por esse motivo, desenhos são ideais para planos de fundo e clip-art.  
  
<a name="drawingvisual_host_container"></a>   
## <a name="drawingvisual-host-container"></a>Contêiner de host do DrawingVisual  
 Para usar <xref:System.Windows.Media.DrawingVisual> objetos, você precisa criar um contêiner de host para os objetos. O objeto contêiner host deve derivar do <xref:System.Windows.FrameworkElement> classe, que oferece suportam a layout e manipulação de eventos a que o <xref:System.Windows.Media.DrawingVisual> carece de classe. O objeto do contêiner de host não exibe nenhuma propriedade visível, já que sua função principal é conter objetos filho. No entanto, o <xref:System.Windows.UIElement.Visibility%2A> propriedade do contêiner host deve ser definida como <xref:System.Windows.Visibility.Visible>; caso contrário, nenhum de seus elementos filho será visível.  
  
 Quando você cria um objeto de contêiner de host para objetos visuais, você precisa armazenar as referências de objeto visual em um <xref:System.Windows.Media.VisualCollection>. Use o <xref:System.Windows.Media.VisualCollection.Add%2A> método para adicionar um objeto visual ao contêiner de host. No exemplo a seguir, um objeto de host do contêiner é criado e três objetos visuais são adicionados ao seu <xref:System.Windows.Media.VisualCollection>.  
  
 [!code-csharp[DrawingVisualSample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[DrawingVisualSample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#100)]  
  
> [!NOTE]
>  Para o exemplo de código completo do qual o exemplo de código anterior foi extraído, consulte [Exemplo de teste de clique usando DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
<a name="creating_drawingvisual_objects"></a>   
## <a name="creating-drawingvisual-objects"></a>Criando objetos DrawingVisual  
 Quando você cria um <xref:System.Windows.Media.DrawingVisual> do objeto, ele não tem nenhum conteúdo de desenho. Você pode adicionar texto, gráficos ou conteúdo de imagem Recuperando do objeto <xref:System.Windows.Media.DrawingContext> e desenhando nele. Um <xref:System.Windows.Media.DrawingContext> é retornado ao chamar o <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A> método de um <xref:System.Windows.Media.DrawingVisual> objeto.  
  
 Para desenhar um retângulo para o <xref:System.Windows.Media.DrawingContext>, usar o <xref:System.Windows.Media.DrawingContext.DrawRectangle%2A> método da <xref:System.Windows.Media.DrawingContext> objeto. Existem métodos semelhantes para desenhar outros tipos de conteúdo. Quando você terminar de desenhar conteúdo para o <xref:System.Windows.Media.DrawingContext>, chamar o <xref:System.Windows.Media.DrawingContext.Close%2A> método para fechar o <xref:System.Windows.Media.DrawingContext> e persistir o conteúdo.  
  
 No exemplo a seguir, uma <xref:System.Windows.Media.DrawingVisual> objeto é criado e um retângulo é desenhado no seu <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[DrawingVisualSample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[DrawingVisualSample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
<a name="creating_overrides"></a>   
## <a name="creating-overrides-for-frameworkelement-members"></a>Criando substituições para membros FrameworkElement  
 O objeto do contêiner de host é responsável por gerenciar sua coleção de objetos visuais. Isso requer que o contêiner de host implemente substituições de membros para a derivada <xref:System.Windows.FrameworkElement> classe.  
  
 A lista a seguir descreve os dois membros que você deve substituir:  
  
-   <xref:System.Windows.FrameworkElement.GetVisualChild%2A>: Retorna um filho no índice especificado da coleção de elementos filho.  
  
-   <xref:System.Windows.FrameworkElement.VisualChildrenCount%2A>: Obtém o número de elementos filho visuais dentro desse elemento.  
  
 No exemplo a seguir, substituições para os dois <xref:System.Windows.FrameworkElement> membros são implementados.  
  
 [!code-csharp[DrawingVisualSample#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#102)]
 [!code-vb[DrawingVisualSample#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#102)]  
  
<a name="providing_hit_testing_support"></a>   
## <a name="providing-hit-testing-support"></a>Fornecendo suporte a teste de clique  
 O objeto contêiner host pode fornecer manipulação de eventos, mesmo se ele não exibe nenhuma propriedade visível — no entanto, sua <xref:System.Windows.UIElement.Visibility%2A> propriedade deve ser definida como <xref:System.Windows.Visibility.Visible>. Isso permite que você crie uma rotina de manipulação de evento para o contêiner de host que pode capturar eventos de mouse, como a liberação do botão esquerdo do mouse. A rotina de manipulação de eventos, em seguida, podem implementar teste de clique ao invocar o <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> método. O método <xref:System.Windows.Media.HitTestResultCallback> parâmetro faz referência a um procedimento definido pelo usuário que você pode usar para determinar a ação resultante de um teste de clique.  
  
 No exemplo a seguir, o suporte para teste de clique é implementado para o objeto do contêiner de host e seus filhos.  
  
 [!code-csharp[DrawingVisualSample#103](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#103)]
 [!code-vb[DrawingVisualSample#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#103)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.DrawingVisual>
- <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A>
- [Visão geral de renderização de gráficos do WPF](wpf-graphics-rendering-overview.md)
- [Teste de clique na camada visual](hit-testing-in-the-visual-layer.md)
