---
title: Visão geral de adornos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111173"
---
# <a name="adorners-overview"></a>Visão geral de adornos

Adornos são um <xref:System.Windows.FrameworkElement>tipo especial de , usado para fornecer pistas visuais para um usuário. Entre outros usos, adornos podem ser usados para adicionar alças funcionais a elementos ou para fornecer informações de estado sobre um controle.

## <a name="about-adorners"></a>Sobre adornos

Um <xref:System.Windows.Documents.Adorner> é <xref:System.Windows.FrameworkElement> um costume que <xref:System.Windows.UIElement>está vinculado a um . Os adornos são <xref:System.Windows.Documents.AdornerLayer>renderizados em uma superfície de renderização que está sempre em cima do elemento adornado ou uma coleção de elementos adornados. A renderização de um adorno <xref:System.Windows.UIElement> é independente da renderização do que o adorno está vinculado. Um adorno é tipicamente posicionado em relação ao elemento ao qual está vinculado, usando a origem padrão de coordenadas 2D localizada no canto superior esquerdo do elemento adornado.

Aplicações comuns de adornos incluem:

- Adicionar alças funcionais a um <xref:System.Windows.UIElement> que permite ao usuário manipular o elemento de alguma forma (redimensionar, girar, reposicionar, etc.).
- Fornecer comentários visuais para indicar vários estados ou em resposta a vários eventos.
- Sobrepor decorações visuais <xref:System.Windows.UIElement>em um .
- Máscara visual ou substituição de parte <xref:System.Windows.UIElement>ou de todos os a .

O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma estrutura básica para o adorno de elementos visuais. A tabela a seguir lista os tipos primários usados ao adornar objetos e sua finalidade. Vários exemplos de uso seguem:

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|Uma classe base abstrata da qual todas as implementações concretas de adornos herdam.|
|<xref:System.Windows.Documents.AdornerLayer>|Uma classe representando uma camada de renderização para os adornos de um ou mais elementos adornados.|
|<xref:System.Windows.Documents.AdornerDecorator>|Uma classe que habilita a associação da camada do adorno a uma coleção de elementos.|

## <a name="implementing-a-custom-adorner"></a>Implementando um adorno personalizado

A estrutura de adornos fornecida por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] destina-se principalmente a dar suporte à criação de adornos personalizados. Um adorno personalizado é criado implementando uma classe <xref:System.Windows.Documents.Adorner> que herda da classe abstrata.

> [!NOTE]
> O pai <xref:System.Windows.Documents.Adorner> de <xref:System.Windows.Documents.AdornerLayer> um é <xref:System.Windows.Documents.Adorner>o que torna o , não o elemento que está sendo adornado.

O exemplo a seguir mostra uma classe que implementa um adorno simples. O exemplo do adorno simplesmente <xref:System.Windows.UIElement> adorna os cantos de um com círculos.

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
A imagem a seguir mostra o SimpleCircleAdorner aplicado a: <xref:System.Windows.Controls.TextBox>

![Captura de tela que mostra uma caixa de texto adornada.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a>Comportamento de renderização para adornos

É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno. Uma maneira comum de implementar o <xref:System.Windows.UIElement.OnRender%2A> comportamento de renderização <xref:System.Windows.Media.DrawingContext> é substituir o método e usar um ou mais objetos para tornar o visual do adorno conforme necessário (como mostrado no exemplo acima).

> [!NOTE]
> Qualquer elemento colocado na camada de adorno é renderizado sobre os demais estilos definidos. Em outras palavras, adornos estão sempre visualmente acima e não podem ser substituídos usando a ordem z.

## <a name="events-and-hit-testing"></a>Eventos e teste de clique

Adornos recebem eventos de <xref:System.Windows.FrameworkElement>entrada como qualquer outro .  Como um adorno sempre tem uma ordem z mais alta do que o <xref:System.Windows.UIElement.Drop> elemento <xref:System.Windows.UIElement.MouseMove>que adorna, o adorno recebe eventos de entrada (como ou ) que podem ser destinados ao elemento adornado subjacente.  Um adorno pode escutar determinados eventos de entrada e passá-los ao elemento adornado subjacente, gerando novamente o evento.

Para habilitar o teste de retoque de passagem <xref:System.Windows.UIElement.IsHitTestVisible%2A> de elementos um adorno, defina a propriedade de teste de batida **como falsa** no adorno.  Para obter mais informações sobre testes de acerto, consulte [Teste de hit na camada visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).

## <a name="adorning-a-single-uielement"></a>Adornado um único UIElement

Para vincular um adorno <xref:System.Windows.UIElement>a um determinado, siga estas etapas:

1. Chame o <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método estático para obter um <xref:System.Windows.Documents.AdornerLayer> objeto para que seja <xref:System.Windows.UIElement> adornado. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>sobe a árvore visual, começando <xref:System.Windows.UIElement>pelo especificado , e retorna a primeira camada de adorno que encontra. (Se nenhuma camada de adorno for encontrada, o método retornará nulo.)

2. Chame <xref:System.Windows.Documents.AdornerLayer.Add%2A> o método para ligar o <xref:System.Windows.UIElement>adorno ao alvo .

 O exemplo a seguir liga um SimpleCircleAdorner <xref:System.Windows.Controls.TextBox> (mostrado acima) a um *myTextBox*chamado :

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.

## <a name="adorning-the-children-of-a-panel"></a>Adornando os filhos de um painel

Para ligar um adorno às <xref:System.Windows.Controls.Panel>crianças de um , siga estas etapas:

1. Chame `static` o <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método para encontrar uma camada de adorno para o elemento cujos filhos devem ser adornados.

2. Enumerar através dos filhos do elemento <xref:System.Windows.Documents.AdornerLayer.Add%2A> pai e chamar o método para ligar um adorno a cada elemento da criança.

O exemplo a seguir liga um SimpleCircleAdorner (mostrado <xref:System.Windows.Controls.StackPanel> acima) aos filhos de um *myStackPanel*chamado :

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Visão geral de formas e desenhos básicos no WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Pintando com imagens, desenhos e visuais](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Visão geral dos objetos de desenho](../graphics-multimedia/drawing-objects-overview.md)
- [Tópicos de como fazer](adorners-how-to-topics.md)
