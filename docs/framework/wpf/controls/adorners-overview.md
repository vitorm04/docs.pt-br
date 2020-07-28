---
title: Visão geral de adornos
description: Saiba mais sobre Windows Presentation Foundation adorners, um tipo especial de FrameworkElement que fornece indicações para um usuário, como identificadores funcionais para elementos.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167728"
---
# <a name="adorners-overview"></a><span data-ttu-id="87f73-103">Visão geral de adornos</span><span class="sxs-lookup"><span data-stu-id="87f73-103">Adorners Overview</span></span>

<span data-ttu-id="87f73-104">Adorners são um tipo especial de <xref:System.Windows.FrameworkElement> , usado para fornecer indicações visuais a um usuário.</span><span class="sxs-lookup"><span data-stu-id="87f73-104">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="87f73-105">Entre outros usos, adornos podem ser usados para adicionar alças funcionais a elementos ou para fornecer informações de estado sobre um controle.</span><span class="sxs-lookup"><span data-stu-id="87f73-105">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="87f73-106">Sobre adornos</span><span class="sxs-lookup"><span data-stu-id="87f73-106">About Adorners</span></span>

<span data-ttu-id="87f73-107">Um <xref:System.Windows.Documents.Adorner> é um personalizado <xref:System.Windows.FrameworkElement> que está associado a um <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="87f73-107">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="87f73-108">Adorners são renderizados em um <xref:System.Windows.Documents.AdornerLayer> , que é uma superfície de renderização que está sempre acima do elemento adornado ou de uma coleção de elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="87f73-108">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="87f73-109">A renderização de um adorno é independente da renderização da <xref:System.Windows.UIElement> qual o adorno está associado.</span><span class="sxs-lookup"><span data-stu-id="87f73-109">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="87f73-110">Um adorno normalmente é posicionado em relação ao elemento ao qual está associado, usando a origem de coordenada 2D padrão localizada no canto superior esquerdo do elemento adornado.</span><span class="sxs-lookup"><span data-stu-id="87f73-110">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="87f73-111">Aplicações comuns de adornos incluem:</span><span class="sxs-lookup"><span data-stu-id="87f73-111">Common applications for adorners include:</span></span>

- <span data-ttu-id="87f73-112">Adicionar identificadores funcionais a um <xref:System.Windows.UIElement> que permite que um usuário manipule o elemento de alguma forma (redimensionar, girar, reposicionar, etc.).</span><span class="sxs-lookup"><span data-stu-id="87f73-112">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="87f73-113">Fornecer comentários visuais para indicar vários estados ou em resposta a vários eventos.</span><span class="sxs-lookup"><span data-stu-id="87f73-113">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="87f73-114">Sobreponha decorações visuais em um <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="87f73-114">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="87f73-115">Mascarar visualmente ou substituir parte ou todos os <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="87f73-115">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

<span data-ttu-id="87f73-116">O [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fornece uma estrutura básica para o adorno de elementos visuais.</span><span class="sxs-lookup"><span data-stu-id="87f73-116">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="87f73-117">A tabela a seguir lista os tipos primários usados ao adornar objetos e sua finalidade.</span><span class="sxs-lookup"><span data-stu-id="87f73-117">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="87f73-118">Vários exemplos de uso a seguir:</span><span class="sxs-lookup"><span data-stu-id="87f73-118">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="87f73-119">Uma classe base abstrata da qual todas as implementações concretas de adornos herdam.</span><span class="sxs-lookup"><span data-stu-id="87f73-119">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="87f73-120">Uma classe representando uma camada de renderização para os adornos de um ou mais elementos adornados.</span><span class="sxs-lookup"><span data-stu-id="87f73-120">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="87f73-121">Uma classe que habilita a associação da camada do adorno a uma coleção de elementos.</span><span class="sxs-lookup"><span data-stu-id="87f73-121">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="87f73-122">Implementando um adorno personalizado</span><span class="sxs-lookup"><span data-stu-id="87f73-122">Implementing a Custom Adorner</span></span>

<span data-ttu-id="87f73-123">A estrutura de adornos fornecida por [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] destina-se principalmente a dar suporte à criação de adornos personalizados.</span><span class="sxs-lookup"><span data-stu-id="87f73-123">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="87f73-124">Um adorno personalizado é criado pela implementação de uma classe que herda da <xref:System.Windows.Documents.Adorner> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="87f73-124">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="87f73-125">O pai de um <xref:System.Windows.Documents.Adorner> é o <xref:System.Windows.Documents.AdornerLayer> que renderiza o <xref:System.Windows.Documents.Adorner> , não o elemento que está sendo adornado.</span><span class="sxs-lookup"><span data-stu-id="87f73-125">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="87f73-126">O exemplo a seguir mostra uma classe que implementa um adorno simples.</span><span class="sxs-lookup"><span data-stu-id="87f73-126">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="87f73-127">O adorno de exemplo simplesmente adorna os cantos de um <xref:System.Windows.UIElement> com círculos.</span><span class="sxs-lookup"><span data-stu-id="87f73-127">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="87f73-128">A imagem a seguir mostra o SimpleCircleAdorner aplicado a um <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="87f73-128">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Captura de tela que mostra uma caixa de texto adornada.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="87f73-130">Comportamento de renderização para adornos</span><span class="sxs-lookup"><span data-stu-id="87f73-130">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="87f73-131">É importante observar que adornos não incluem nenhum comportamento de renderização inerente; garantir que um adorno seja renderizado é responsabilidade do implementador do adorno.</span><span class="sxs-lookup"><span data-stu-id="87f73-131">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="87f73-132">Uma maneira comum de implementar o comportamento de renderização é substituir o <xref:System.Windows.UIElement.OnRender%2A> método e usar um ou mais <xref:System.Windows.Media.DrawingContext> objetos para renderizar os visuais do adorno conforme necessário (conforme mostrado no exemplo acima).</span><span class="sxs-lookup"><span data-stu-id="87f73-132">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="87f73-133">Qualquer elemento colocado na camada de adorno é renderizado sobre os demais estilos definidos.</span><span class="sxs-lookup"><span data-stu-id="87f73-133">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="87f73-134">Em outras palavras, adornos estão sempre visualmente acima e não podem ser substituídos usando a ordem z.</span><span class="sxs-lookup"><span data-stu-id="87f73-134">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="87f73-135">Eventos e teste de clique</span><span class="sxs-lookup"><span data-stu-id="87f73-135">Events and Hit Testing</span></span>

<span data-ttu-id="87f73-136">Adorners recebem eventos de entrada assim como qualquer outro <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="87f73-136">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="87f73-137">Como um adorno sempre tem uma ordem z maior do que o elemento adornado, o adorno recebe eventos de entrada (como <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove> ) que podem ser destinados ao elemento adornado subjacente.</span><span class="sxs-lookup"><span data-stu-id="87f73-137">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="87f73-138">Um adorno pode escutar determinados eventos de entrada e passá-los ao elemento adornado subjacente, gerando novamente o evento.</span><span class="sxs-lookup"><span data-stu-id="87f73-138">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="87f73-139">Para habilitar o teste de clique de passagem de elementos em um adorno, defina a propriedade de teste de clique <xref:System.Windows.UIElement.IsHitTestVisible%2A> como **false** no adorno.</span><span class="sxs-lookup"><span data-stu-id="87f73-139">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="87f73-140">Para obter mais informações sobre testes de clique, consulte [teste de clique na camada Visual](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="87f73-140">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="87f73-141">Adornado um único UIElement</span><span class="sxs-lookup"><span data-stu-id="87f73-141">Adorning a Single UIElement</span></span>

<span data-ttu-id="87f73-142">Para associar um adorno a um específico <xref:System.Windows.UIElement> , siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="87f73-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="87f73-143">Chame o método estático <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para obter um <xref:System.Windows.Documents.AdornerLayer> objeto para o <xref:System.Windows.UIElement> a ser adornado.</span><span class="sxs-lookup"><span data-stu-id="87f73-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="87f73-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>percorre a árvore visual, começando pelo especificado <xref:System.Windows.UIElement> e retorna a primeira camada de adorno que encontrar.</span><span class="sxs-lookup"><span data-stu-id="87f73-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="87f73-145">(Se nenhuma camada de adorno for encontrada, o método retornará nulo.)</span><span class="sxs-lookup"><span data-stu-id="87f73-145">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="87f73-146">Chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar o adorno ao destino <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="87f73-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="87f73-147">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) a um <xref:System.Windows.Controls.TextBox> *myTextBox*nomeado:</span><span class="sxs-lookup"><span data-stu-id="87f73-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="87f73-148">No momento, não há suporte para usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para associar um adorno a outro elemento.</span><span class="sxs-lookup"><span data-stu-id="87f73-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="87f73-149">Adornando os filhos de um painel</span><span class="sxs-lookup"><span data-stu-id="87f73-149">Adorning the Children of a Panel</span></span>

<span data-ttu-id="87f73-150">Para associar um adorno aos filhos de a <xref:System.Windows.Controls.Panel> , siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="87f73-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="87f73-151">Chame o `static` método <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> para localizar uma camada de adorno para o elemento cujos filhos devem ser adornados.</span><span class="sxs-lookup"><span data-stu-id="87f73-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="87f73-152">Enumere os filhos do elemento pai e chame o <xref:System.Windows.Documents.AdornerLayer.Add%2A> método para associar um adorno a cada elemento filho.</span><span class="sxs-lookup"><span data-stu-id="87f73-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="87f73-153">O exemplo a seguir associa um SimpleCircleAdorner (mostrado acima) aos filhos de um <xref:System.Windows.Controls.StackPanel> chamado *myStackPanel*:</span><span class="sxs-lookup"><span data-stu-id="87f73-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="87f73-154">Confira também</span><span class="sxs-lookup"><span data-stu-id="87f73-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="87f73-155">Visão geral de formas e desenho básico no WPF</span><span class="sxs-lookup"><span data-stu-id="87f73-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="87f73-156">Pintando com imagens, desenhos e visuais</span><span class="sxs-lookup"><span data-stu-id="87f73-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="87f73-157">Visão geral dos objetos de desenho</span><span class="sxs-lookup"><span data-stu-id="87f73-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="87f73-158">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="87f73-158">How-to Topics</span></span>](adorners-how-to-topics.md)
