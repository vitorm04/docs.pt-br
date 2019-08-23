---
title: Visão geral de adornos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: d8e6e53edc92a2847c001377706d313cf97cced5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956103"
---
# <a name="adorners-overview"></a>Visão geral de adornos
Adorners são um tipo especial de <xref:System.Windows.FrameworkElement>, usado para fornecer indicações visuais a um usuário. Entre outros usos, adornos podem ser usados para adicionar alças funcionais a elementos ou para fornecer informações de estado sobre um controle.  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>Sobre adornos  
 Um <xref:System.Windows.Documents.Adorner> é um personalizado <xref:System.Windows.FrameworkElement> que está associado a um <xref:System.Windows.UIElement>. Adorners são renderizados em <xref:System.Windows.Documents.AdornerLayer>um, que é uma superfície de renderização que está sempre acima do elemento adornado ou de uma coleção de elementos adornados. A renderização de um adorno é independente da renderização da <xref:System.Windows.UIElement> qual o adorno está associado. Um adorno geralmente é posicionado em relação ao elemento ao qual ele está vinculado, usando a origem de coordenada 2D padrão localizada no canto superior esquerdo do elemento adornado.  
  
 Aplicações comuns de adornos incluem:  
  
- Adicionar identificadores funcionais a <xref:System.Windows.UIElement> um que permite que um usuário manipule o elemento de alguma forma (redimensionar, girar, reposicionar, etc.).  
  
- Fornecer comentários visuais para indicar vários estados ou em resposta a vários eventos.  
  
- Sobreponha decorações visuais em <xref:System.Windows.UIElement>um.  
  
- Mascarar visualmente ou substituir parte ou todos <xref:System.Windows.UIElement>os.  
  
 O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma estrutura básica para o adorno de elementos visuais. A tabela a seguir lista os tipos primários usados ao adornar objetos e sua finalidade. A seguir, são apresentados vários exemplos de uso.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Uma classe base abstrata da qual todas as implementações concretas de adornos herdam.|  
|<xref:System.Windows.Documents.AdornerLayer>|Uma classe representando uma camada de renderização para os adornos de um ou mais elementos adornados.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Uma classe que habilita a associação da camada do adorno a uma coleção de elementos.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implementando um adorno personalizado  
 A estrutura de adornos fornecida por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] destina-se principalmente a dar suporte à criação de adornos personalizados. Um adorno personalizado é criado pela implementação de uma classe que herda da classe <xref:System.Windows.Documents.Adorner> abstrata.  
  
> [!NOTE]
> O pai de um <xref:System.Windows.Documents.Adorner> é o <xref:System.Windows.Documents.AdornerLayer> que renderiza o <xref:System.Windows.Documents.Adorner>, não o elemento que está sendo adornado.  
  
 O exemplo a seguir mostra uma classe que implementa um adorno simples. O adorno de exemplo simplesmente adorna os cantos de um <xref:System.Windows.UIElement> com círculos.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 A imagem a seguir mostra o SimpleCircleAdorner aplicado a <xref:System.Windows.Controls.TextBox>um.  
  
 ![Captura de tela que mostra uma caixa de texto adornada.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Comportamento de renderização para adornos  
 É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.   Uma maneira comum de implementar o comportamento de renderização é substituir <xref:System.Windows.UIElement.OnRender%2A> o método e usar um ou <xref:System.Windows.Media.DrawingContext> mais objetos para renderizar os visuais do adorno conforme necessário (conforme mostrado no exemplo acima).  
  
> [!NOTE]
> Qualquer elemento colocado na camada de adorno é renderizado sobre os demais estilos definidos. Em outras palavras, adornos estão sempre visualmente acima e não podem ser substituídos usando a ordem z.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Eventos e teste de clique  
 Adorners recebem eventos de entrada assim como qualquer <xref:System.Windows.FrameworkElement>outro.  Como um adorno sempre tem uma ordem z maior do que o elemento adornado, o adorno recebe eventos de entrada ( <xref:System.Windows.UIElement.Drop> como ou <xref:System.Windows.UIElement.MouseMove>) que podem ser destinados ao elemento adornado subjacente.  Um adorno pode escutar determinados eventos de entrada e passá-los ao elemento adornado subjacente, gerando novamente o evento.  
  
 Para habilitar o teste de clique de passagem de elementos em um adorno, defina a propriedade <xref:System.Windows.UIElement.IsHitTestVisible%2A> de teste de clique como **false** no adorno.  Para obter mais informações sobre teste de clique, consulte  
  
 [Teste de clique na camada visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Adornado um único UIElement  
 Para associar um adorno a um específico <xref:System.Windows.UIElement>, siga estas etapas:  
  
1. Chame o método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> estático para obter um <xref:System.Windows.Documents.AdornerLayer> objeto para o <xref:System.Windows.UIElement> a ser adornado. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>percorre a árvore visual, começando pelo especificado <xref:System.Windows.UIElement>e retorna a primeira camada de adorno que encontrar. (Se nenhuma camada de adorno for encontrada, o método retornará nulo.)  
  
2. Chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino <xref:System.Windows.UIElement>.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) a um <xref:System.Windows.Controls.TextBox> *myTextBox*nomeado.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Adornando os filhos de um painel  
 Para associar um adorno aos filhos de a <xref:System.Windows.Controls.Panel>, siga estas etapas:  
  
1. Chame o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para localizar uma camada de adorno para o elemento cujos filhos devem ser adornados.  
  
2. Enumere os filhos do elemento pai e chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.  
  
 O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> chamado myStackPanel.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Visão geral de formas e desenho básico no WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Pintando com imagens, desenhos e visuais](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Visão geral dos objetos de desenho](../graphics-multimedia/drawing-objects-overview.md)
- [Tópicos de instruções](adorners-how-to-topics.md)
