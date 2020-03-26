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
# <a name="adorners-overview"></a><span data-ttu-id="5a28c-102">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="5a28c-102">Adorners Overview</span></span>

<span data-ttu-id="5a28c-103">Adornos são um <xref:System.Windows.FrameworkElement>tipo especial de , usado para fornecer pistas visuais para um usuário.</span><span class="sxs-lookup"><span data-stu-id="5a28c-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="5a28c-104">Entre outros usos, adornos podem ser usados para adicionar alças funcionais a elementos ou para fornecer informações de estado sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="5a28c-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="5a28c-105">Sobre adornos</span><span class="sxs-lookup"><span data-stu-id="5a28c-105">About Adorners</span></span>

<span data-ttu-id="5a28c-106">Um <xref:System.Windows.Documents.Adorner> é <xref:System.Windows.FrameworkElement> um costume que <xref:System.Windows.UIElement>está vinculado a um .</span><span class="sxs-lookup"><span data-stu-id="5a28c-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="5a28c-107">Os adornos são <xref:System.Windows.Documents.AdornerLayer>renderizados em uma superfície de renderização que está sempre em cima do elemento adornado ou uma coleção de elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="5a28c-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="5a28c-108">A renderização de um adorno <xref:System.Windows.UIElement> é independente da renderização do que o adorno está vinculado.</span><span class="sxs-lookup"><span data-stu-id="5a28c-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="5a28c-109">Um adorno é tipicamente posicionado em relação ao elemento ao qual está vinculado, usando a origem padrão de coordenadas 2D localizada no canto superior esquerdo do elemento adornado.</span><span class="sxs-lookup"><span data-stu-id="5a28c-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="5a28c-110">Aplicações comuns de adornos incluem:</span><span class="sxs-lookup"><span data-stu-id="5a28c-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="5a28c-111">Adicionar alças funcionais a um <xref:System.Windows.UIElement> que permite ao usuário manipular o elemento de alguma forma (redimensionar, girar, reposicionar, etc.).</span><span class="sxs-lookup"><span data-stu-id="5a28c-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="5a28c-112">Fornecer comentários visuais para indicar vários estados ou em resposta a vários eventos.</span><span class="sxs-lookup"><span data-stu-id="5a28c-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="5a28c-113">Sobrepor decorações visuais <xref:System.Windows.UIElement>em um .</span><span class="sxs-lookup"><span data-stu-id="5a28c-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="5a28c-114">Máscara visual ou substituição de parte <xref:System.Windows.UIElement>ou de todos os a .</span><span class="sxs-lookup"><span data-stu-id="5a28c-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

<span data-ttu-id="5a28c-115">O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma estrutura básica para o adorno de elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="5a28c-115">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="5a28c-116">A tabela a seguir lista os tipos primários usados ao adornar objetos e sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="5a28c-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="5a28c-117">Vários exemplos de uso seguem:</span><span class="sxs-lookup"><span data-stu-id="5a28c-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="5a28c-118">Uma classe base abstrata da qual todas as implementações concretas de adornos herdam.</span><span class="sxs-lookup"><span data-stu-id="5a28c-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="5a28c-119">Uma classe representando uma camada de renderização para os adornos de um ou mais elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="5a28c-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="5a28c-120">Uma classe que habilita a associação da camada do adorno a uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="5a28c-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="5a28c-121">Implementando um adorno personalizado</span><span class="sxs-lookup"><span data-stu-id="5a28c-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="5a28c-122">A estrutura de adornos fornecida por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] destina-se principalmente a dar suporte à criação de adornos personalizados.</span><span class="sxs-lookup"><span data-stu-id="5a28c-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="5a28c-123">Um adorno personalizado é criado implementando uma classe <xref:System.Windows.Documents.Adorner> que herda da classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="5a28c-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="5a28c-124">O pai <xref:System.Windows.Documents.Adorner> de <xref:System.Windows.Documents.AdornerLayer> um é <xref:System.Windows.Documents.Adorner>o que torna o , não o elemento que está sendo adornado.</span><span class="sxs-lookup"><span data-stu-id="5a28c-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="5a28c-125">O exemplo a seguir mostra uma classe que implementa um adorno simples.</span><span class="sxs-lookup"><span data-stu-id="5a28c-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="5a28c-126">O exemplo do adorno simplesmente <xref:System.Windows.UIElement> adorna os cantos de um com círculos.</span><span class="sxs-lookup"><span data-stu-id="5a28c-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="5a28c-127">A imagem a seguir mostra o SimpleCircleAdorner aplicado a: <xref:System.Windows.Controls.TextBox></span><span class="sxs-lookup"><span data-stu-id="5a28c-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Captura de tela que mostra uma caixa de texto adornada.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="5a28c-129">Comportamento de renderização para adornos</span><span class="sxs-lookup"><span data-stu-id="5a28c-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="5a28c-130">É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.</span><span class="sxs-lookup"><span data-stu-id="5a28c-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="5a28c-131">Uma maneira comum de implementar o <xref:System.Windows.UIElement.OnRender%2A> comportamento de renderização <xref:System.Windows.Media.DrawingContext> é substituir o método e usar um ou mais objetos para tornar o visual do adorno conforme necessário (como mostrado no exemplo acima).</span><span class="sxs-lookup"><span data-stu-id="5a28c-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="5a28c-132">Qualquer elemento colocado na camada de adorno é renderizado sobre os demais estilos definidos.</span><span class="sxs-lookup"><span data-stu-id="5a28c-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="5a28c-133">Em outras palavras, adornos estão sempre visualmente acima e não podem ser substituídos usando a ordem z.</span><span class="sxs-lookup"><span data-stu-id="5a28c-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="5a28c-134">Eventos e teste de clique</span><span class="sxs-lookup"><span data-stu-id="5a28c-134">Events and Hit Testing</span></span>

<span data-ttu-id="5a28c-135">Adornos recebem eventos de <xref:System.Windows.FrameworkElement>entrada como qualquer outro .</span><span class="sxs-lookup"><span data-stu-id="5a28c-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="5a28c-136">Como um adorno sempre tem uma ordem z mais alta do que o <xref:System.Windows.UIElement.Drop> elemento <xref:System.Windows.UIElement.MouseMove>que adorna, o adorno recebe eventos de entrada (como ou ) que podem ser destinados ao elemento adornado subjacente.</span><span class="sxs-lookup"><span data-stu-id="5a28c-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="5a28c-137">Um adorno pode escutar determinados eventos de entrada e passá-los ao elemento adornado subjacente, gerando novamente o evento.</span><span class="sxs-lookup"><span data-stu-id="5a28c-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="5a28c-138">Para habilitar o teste de retoque de passagem <xref:System.Windows.UIElement.IsHitTestVisible%2A> de elementos um adorno, defina a propriedade de teste de batida **como falsa** no adorno.</span><span class="sxs-lookup"><span data-stu-id="5a28c-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="5a28c-139">Para obter mais informações sobre testes de acerto, consulte [Teste de hit na camada visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="5a28c-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="5a28c-140">Adornado um único UIElement</span><span class="sxs-lookup"><span data-stu-id="5a28c-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="5a28c-141">Para vincular um adorno <xref:System.Windows.UIElement>a um determinado, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="5a28c-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="5a28c-142">Chame o <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método estático para obter um <xref:System.Windows.Documents.AdornerLayer> objeto para que seja <xref:System.Windows.UIElement> adornado.</span><span class="sxs-lookup"><span data-stu-id="5a28c-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="5a28c-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>sobe a árvore visual, começando <xref:System.Windows.UIElement>pelo especificado , e retorna a primeira camada de adorno que encontra.</span><span class="sxs-lookup"><span data-stu-id="5a28c-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="5a28c-144">(Se nenhuma camada de adorno for encontrada, o método retornará nulo.)</span><span class="sxs-lookup"><span data-stu-id="5a28c-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="5a28c-145">Chame <xref:System.Windows.Documents.AdornerLayer.Add%2A> o método para ligar o <xref:System.Windows.UIElement>adorno ao alvo .</span><span class="sxs-lookup"><span data-stu-id="5a28c-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="5a28c-146">O exemplo a seguir liga um SimpleCircleAdorner <xref:System.Windows.Controls.TextBox> (mostrado acima) a um *myTextBox*chamado :</span><span class="sxs-lookup"><span data-stu-id="5a28c-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="5a28c-147">No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.</span><span class="sxs-lookup"><span data-stu-id="5a28c-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="5a28c-148">Adornando os filhos de um painel</span><span class="sxs-lookup"><span data-stu-id="5a28c-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="5a28c-149">Para ligar um adorno às <xref:System.Windows.Controls.Panel>crianças de um , siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="5a28c-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="5a28c-150">Chame `static` o <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> método para encontrar uma camada de adorno para o elemento cujos filhos devem ser adornados.</span><span class="sxs-lookup"><span data-stu-id="5a28c-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="5a28c-151">Enumerar através dos filhos do elemento <xref:System.Windows.Documents.AdornerLayer.Add%2A> pai e chamar o método para ligar um adorno a cada elemento da criança.</span><span class="sxs-lookup"><span data-stu-id="5a28c-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="5a28c-152">O exemplo a seguir liga um SimpleCircleAdorner (mostrado <xref:System.Windows.Controls.StackPanel> acima) aos filhos de um *myStackPanel*chamado :</span><span class="sxs-lookup"><span data-stu-id="5a28c-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="5a28c-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="5a28c-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="5a28c-154">Visão geral de formas e desenhos básicos no WPF</span><span class="sxs-lookup"><span data-stu-id="5a28c-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="5a28c-155">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="5a28c-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="5a28c-156">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="5a28c-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="5a28c-157">Tópicos de como fazer</span><span class="sxs-lookup"><span data-stu-id="5a28c-157">How-to Topics</span></span>](adorners-how-to-topics.md)
