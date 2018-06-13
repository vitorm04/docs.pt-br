---
title: Visão geral de adornos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 6dd38b9e24b42de8945c0e9729f8f30cf901fc3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557115"
---
# <a name="adorners-overview"></a><span data-ttu-id="105f6-102">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="105f6-102">Adorners Overview</span></span>
<span data-ttu-id="105f6-103">Adornos são um tipo especial de <xref:System.Windows.FrameworkElement>, usado para fornecer dicas visuais para um usuário.</span><span class="sxs-lookup"><span data-stu-id="105f6-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="105f6-104">Entre outros usos, adornos podem ser usados para adicionar alças funcionais a elementos ou para fornecer informações de estado sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="105f6-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>  
  
  
  
<a name="about_Adorners"></a>   
## <a name="about-adorners"></a><span data-ttu-id="105f6-105">Sobre adornos</span><span class="sxs-lookup"><span data-stu-id="105f6-105">About Adorners</span></span>  
 <span data-ttu-id="105f6-106">Um <xref:System.Windows.Documents.Adorner> é um personalizado <xref:System.Windows.FrameworkElement> que está associado a um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="105f6-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="105f6-107">Adornos são renderizados em um <xref:System.Windows.Documents.AdornerLayer>, que é uma superfície de renderização que sempre está acima do elemento adornado ou uma coleção de elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="105f6-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="105f6-108">Renderização de um adorno é independente da renderização do <xref:System.Windows.UIElement> que o qual ele está associado.</span><span class="sxs-lookup"><span data-stu-id="105f6-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="105f6-109">Um adorno geralmente é posicionado em relação ao elemento ao qual ele está vinculado, usando a origem de coordenada 2D padrão localizada no canto superior esquerdo do elemento adornado.</span><span class="sxs-lookup"><span data-stu-id="105f6-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2-D coordinate origin located at the upper-left of the adorned element.</span></span>  
  
 <span data-ttu-id="105f6-110">Aplicações comuns de adornos incluem:</span><span class="sxs-lookup"><span data-stu-id="105f6-110">Common applications for adorners include:</span></span>  
  
-   <span data-ttu-id="105f6-111">Adicionando identificadores funcionais para uma <xref:System.Windows.UIElement> que permitem ao usuário manipular o elemento de alguma forma (girar, redimensionar, reposicionar, etc.).</span><span class="sxs-lookup"><span data-stu-id="105f6-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>  
  
-   <span data-ttu-id="105f6-112">Fornecer comentários visuais para indicar vários estados ou em resposta a vários eventos.</span><span class="sxs-lookup"><span data-stu-id="105f6-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>  
  
-   <span data-ttu-id="105f6-113">Sobrepor decorações visuais em um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="105f6-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>  
  
-   <span data-ttu-id="105f6-114">Visualmente mascarar ou anular parte ou todo um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="105f6-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="105f6-115">O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma estrutura básica para o adorno de elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="105f6-115">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="105f6-116">A tabela a seguir lista os tipos primários usados ao adornar objetos e sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="105f6-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="105f6-117">A seguir, são apresentados vários exemplos de uso.</span><span class="sxs-lookup"><span data-stu-id="105f6-117">Several usage examples follow.</span></span>  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="105f6-118">Uma classe base abstrata da qual todas as implementações concretas de adornos herdam.</span><span class="sxs-lookup"><span data-stu-id="105f6-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|  
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="105f6-119">Uma classe representando uma camada de renderização para os adornos de um ou mais elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="105f6-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|  
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="105f6-120">Uma classe que habilita a associação da camada do adorno a uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="105f6-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="105f6-121">Implementando um adorno personalizado</span><span class="sxs-lookup"><span data-stu-id="105f6-121">Implementing a Custom Adorner</span></span>  
 <span data-ttu-id="105f6-122">A estrutura de adornos fornecida por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] destina-se principalmente a dar suporte à criação de adornos personalizados.</span><span class="sxs-lookup"><span data-stu-id="105f6-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="105f6-123">Um adorno personalizado é criado com a implementação de uma classe que herda da <xref:System.Windows.Documents.Adorner> classe.</span><span class="sxs-lookup"><span data-stu-id="105f6-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="105f6-124">O pai de um <xref:System.Windows.Documents.Adorner> é o <xref:System.Windows.Documents.AdornerLayer> que renderiza o <xref:System.Windows.Documents.Adorner>, não o elemento sendo adornado.</span><span class="sxs-lookup"><span data-stu-id="105f6-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>  
  
 <span data-ttu-id="105f6-125">O exemplo a seguir mostra uma classe que implementa um adorno simples.</span><span class="sxs-lookup"><span data-stu-id="105f6-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="105f6-126">O adorno de exemplo simplesmente adorna os cantos de uma <xref:System.Windows.UIElement> com círculos.</span><span class="sxs-lookup"><span data-stu-id="105f6-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 <span data-ttu-id="105f6-127">A imagem a seguir mostra o SimpleCircleAdorner aplicado a um <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="105f6-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
 <span data-ttu-id="105f6-128">![Exemplo de adornos: uma TextBox adornada](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span><span class="sxs-lookup"><span data-stu-id="105f6-128">![Adorners Example: An adorned TextBox](../../../../docs/framework/wpf/controls/media/adornedtextbox.png "AdornedTextBox")</span></span>  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="105f6-129">Comportamento de renderização para adornos</span><span class="sxs-lookup"><span data-stu-id="105f6-129">Rendering Behavior for Adorners</span></span>  
 <span data-ttu-id="105f6-130">É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.</span><span class="sxs-lookup"><span data-stu-id="105f6-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="105f6-131">Uma maneira comum de implementar o comportamento de renderização é substituir a <xref:System.Windows.UIElement.OnRender%2A> método e o uso de um ou mais <xref:System.Windows.Media.DrawingContext> objetos para renderizar os visuais do adorno conforme necessário (como mostrado no exemplo acima).</span><span class="sxs-lookup"><span data-stu-id="105f6-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="105f6-132">Qualquer elemento colocado na camada de adorno é renderizado sobre os demais estilos definidos.</span><span class="sxs-lookup"><span data-stu-id="105f6-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="105f6-133">Em outras palavras, adornos estão sempre visualmente acima e não podem ser substituídos usando a ordem z.</span><span class="sxs-lookup"><span data-stu-id="105f6-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a><span data-ttu-id="105f6-134">Eventos e teste de clique</span><span class="sxs-lookup"><span data-stu-id="105f6-134">Events and Hit Testing</span></span>  
 <span data-ttu-id="105f6-135">Adornos recebem eventos de entrada assim como qualquer outro <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="105f6-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="105f6-136">Como um adorno sempre tem uma ordem z maior que o elemento adorna por ele, o adorno recebe eventos de entrada (como <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove>) que podem ser direcionados para o elemento adornado subjacente.</span><span class="sxs-lookup"><span data-stu-id="105f6-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="105f6-137">Um adorno pode escutar determinados eventos de entrada e passá-los ao elemento adornado subjacente, gerando novamente o evento.</span><span class="sxs-lookup"><span data-stu-id="105f6-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>  
  
 <span data-ttu-id="105f6-138">Para habilitar o teste de clique passagem de elementos em um adorno, defina o teste de clique <xref:System.Windows.UIElement.IsHitTestVisible%2A> propriedade **false** no adorno.</span><span class="sxs-lookup"><span data-stu-id="105f6-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="105f6-139">Para obter mais informações sobre teste de clique, consulte</span><span class="sxs-lookup"><span data-stu-id="105f6-139">For more information about hit testing, see</span></span>  
  
 <span data-ttu-id="105f6-140">[Teste de clique na camada visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="105f6-140">[Hit Testing in the Visual Layer](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a><span data-ttu-id="105f6-141">Adornado um único UIElement</span><span class="sxs-lookup"><span data-stu-id="105f6-141">Adorning a Single UIElement</span></span>  
 <span data-ttu-id="105f6-142">Para associar um adorno a um determinado <xref:System.Windows.UIElement>, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="105f6-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="105f6-143">Chame o método estático <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter um <xref:System.Windows.Documents.AdornerLayer> de objeto para o <xref:System.Windows.UIElement> adornados.</span><span class="sxs-lookup"><span data-stu-id="105f6-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="105f6-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> percorre a árvore visual, iniciando no elemento <xref:System.Windows.UIElement>e retorna a primeira camada de adorno que encontrar.</span><span class="sxs-lookup"><span data-stu-id="105f6-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="105f6-145">(Se nenhuma camada de adorno for encontrada, o método retornará nulo.)</span><span class="sxs-lookup"><span data-stu-id="105f6-145">(If no adorner layers are found, the method returns null.)</span></span>  
  
2.  <span data-ttu-id="105f6-146">Chamar o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="105f6-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>  
  
 <span data-ttu-id="105f6-147">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) a um <xref:System.Windows.Controls.TextBox> chamado *myTextBox*.</span><span class="sxs-lookup"><span data-stu-id="105f6-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  <span data-ttu-id="105f6-148">No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.</span><span class="sxs-lookup"><span data-stu-id="105f6-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="105f6-149">Adornando os filhos de um painel</span><span class="sxs-lookup"><span data-stu-id="105f6-149">Adorning the Children of a Panel</span></span>  
 <span data-ttu-id="105f6-150">Para associar um adorno aos filhos de um <xref:System.Windows.Controls.Panel>, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="105f6-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1.  <span data-ttu-id="105f6-151">Chamar o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para encontrar uma camada de adorno para o elemento cujos filhos serão adornados.</span><span class="sxs-lookup"><span data-stu-id="105f6-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2.  <span data-ttu-id="105f6-152">Enumerar todos os filhos do elemento pai e chamada de <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="105f6-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="105f6-153">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> chamado *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="105f6-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a><span data-ttu-id="105f6-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="105f6-154">See Also</span></span>  
 <xref:System.Windows.Media.AdornerHitTestResult>  
 [<span data-ttu-id="105f6-155">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="105f6-155">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="105f6-156">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="105f6-156">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="105f6-157">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="105f6-157">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="105f6-158">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="105f6-158">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/adorners-how-to-topics.md)
