---
title: 'Como: Definir uma propriedade depois de animá-la com um Storyboard'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 593d3fcefe3bb81518d0886afde82f9a172874ba
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912382"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a><span data-ttu-id="0fc04-102">Como: Definir uma propriedade depois de animá-la com um Storyboard</span><span class="sxs-lookup"><span data-stu-id="0fc04-102">How to: Set a Property After Animating It with a Storyboard</span></span>
<span data-ttu-id="0fc04-103">Em alguns casos, pode parecer que não é possível alterar o valor de uma propriedade depois dela ter sido animada.</span><span class="sxs-lookup"><span data-stu-id="0fc04-103">In some cases, it might appear that you can't change the value of a property after it has been animated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fc04-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fc04-104">Example</span></span>  
 <span data-ttu-id="0fc04-105">No exemplo a seguir, uma <xref:System.Windows.Media.Animation.Storyboard> é usado para animar a cor de um <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="0fc04-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> is used to animate the color of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="0fc04-106">O storyboard é disparado ao clicar no botão.</span><span class="sxs-lookup"><span data-stu-id="0fc04-106">The storyboard is triggered when the button is clicked.</span></span> <span data-ttu-id="0fc04-107">O <xref:System.Windows.Media.Animation.Timeline.Completed> evento é tratado para que o programa seja notificado quando o <xref:System.Windows.Media.Animation.ColorAnimation> é concluída.</span><span class="sxs-lookup"><span data-stu-id="0fc04-107">The <xref:System.Windows.Media.Animation.Timeline.Completed> event is handled so that the program is notified when the <xref:System.Windows.Media.Animation.ColorAnimation> completes.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a><span data-ttu-id="0fc04-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0fc04-108">Example</span></span>  
 <span data-ttu-id="0fc04-109">Após o <xref:System.Windows.Media.Animation.ColorAnimation> for concluído, o programa tenta alterar a cor do pincel para azul.</span><span class="sxs-lookup"><span data-stu-id="0fc04-109">After the <xref:System.Windows.Media.Animation.ColorAnimation> completes, the program attempts to change the brush's color to blue.</span></span>  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 <span data-ttu-id="0fc04-110">O código anterior parece não fazer nada: o pincel permanece amarelo, que é o valor fornecido pelo <xref:System.Windows.Media.Animation.ColorAnimation> que animou o pincel.</span><span class="sxs-lookup"><span data-stu-id="0fc04-110">The previous code doesn't appear to do anything: the brush remains yellow, which is the value supplied by the <xref:System.Windows.Media.Animation.ColorAnimation> that animated the brush.</span></span> <span data-ttu-id="0fc04-111">O valor da propriedade subjacente (o valor de base) é efetivamente alterado para azul.</span><span class="sxs-lookup"><span data-stu-id="0fc04-111">The underlying property value (the base value) is actually changed to blue.</span></span> <span data-ttu-id="0fc04-112">No entanto, o valor efetivo ou atual permanece amarelo porque o <xref:System.Windows.Media.Animation.ColorAnimation> ainda estará substituindo o valor base.</span><span class="sxs-lookup"><span data-stu-id="0fc04-112">However, the effective, or current, value remains yellow because the <xref:System.Windows.Media.Animation.ColorAnimation> is still overriding the base value.</span></span> <span data-ttu-id="0fc04-113">Se desejar que o valor de base se torne o valor efetivo novamente, você deverá impedir que a animação influencie a propriedade.</span><span class="sxs-lookup"><span data-stu-id="0fc04-113">If you want the base value to become the effective value again, you must stop the animation from influencing the property.</span></span> <span data-ttu-id="0fc04-114">Há três maneiras de fazer isso com animações do storyboard:</span><span class="sxs-lookup"><span data-stu-id="0fc04-114">There are three ways to do this with storyboard animations:</span></span>  
  
- <span data-ttu-id="0fc04-115">Definir a animação <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade <xref:System.Windows.Media.Animation.FillBehavior.Stop></span><span class="sxs-lookup"><span data-stu-id="0fc04-115">Set the animation's <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property to <xref:System.Windows.Media.Animation.FillBehavior.Stop></span></span>  
  
- <span data-ttu-id="0fc04-116">Remova todo o storyboard.</span><span class="sxs-lookup"><span data-stu-id="0fc04-116">Remove the entire Storyboard.</span></span>  
  
- <span data-ttu-id="0fc04-117">Remova a animação da propriedade individual.</span><span class="sxs-lookup"><span data-stu-id="0fc04-117">Remove the animation from the individual property.</span></span>  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a><span data-ttu-id="0fc04-118">Definir a propriedade FillBehavior da animação como Parar</span><span class="sxs-lookup"><span data-stu-id="0fc04-118">Set the animation's FillBehavior property to Stop</span></span>  
 <span data-ttu-id="0fc04-119">Definindo <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> para <xref:System.Windows.Media.Animation.FillBehavior.Stop>, você indica que a animação pare de afetar sua propriedade de destino após atingir o final do seu período ativo.</span><span class="sxs-lookup"><span data-stu-id="0fc04-119">By setting <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, you tell the animation to stop affecting its target property after it reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a><span data-ttu-id="0fc04-120">Remover todo o storyboard</span><span class="sxs-lookup"><span data-stu-id="0fc04-120">Remove the entire storyboard</span></span>  
 <span data-ttu-id="0fc04-121">Usando um <xref:System.Windows.Media.Animation.RemoveStoryboard> disparador ou o <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> método, você informa que as animações de storyboard devem parar de afetar suas propriedades de destino.</span><span class="sxs-lookup"><span data-stu-id="0fc04-121">By using a <xref:System.Windows.Media.Animation.RemoveStoryboard> trigger or the <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType> method, you tell the storyboard animations to stop affecting their target properties.</span></span> <span data-ttu-id="0fc04-122">A diferença entre essa abordagem e o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade é que você pode remover o storyboard a qualquer momento, enquanto o <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> propriedade só tem efeito quando a animação atinge o final do seu período ativo.</span><span class="sxs-lookup"><span data-stu-id="0fc04-122">The difference between this approach and setting the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property is that you can remove the storyboard at anytime, while the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property only has an effect when the animation reaches the end of its active period.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a><span data-ttu-id="0fc04-123">Remover uma animação de uma propriedade individual</span><span class="sxs-lookup"><span data-stu-id="0fc04-123">Remove an animation from an individual property</span></span>  
 <span data-ttu-id="0fc04-124">Outra técnica para impedir que uma animação afete uma propriedade é usar o <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> método do objeto que está sendo animado.</span><span class="sxs-lookup"><span data-stu-id="0fc04-124">Another technique to stop an animation from affecting a property is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> method of the object being animated.</span></span> <span data-ttu-id="0fc04-125">Especifique a propriedade sendo animada como o primeiro parâmetro e `null` como o segundo.</span><span class="sxs-lookup"><span data-stu-id="0fc04-125">Specify the property being animated as the first parameter and `null` as the second.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 <span data-ttu-id="0fc04-126">Essa técnica também funciona para animações que não são do storyboard.</span><span class="sxs-lookup"><span data-stu-id="0fc04-126">This technique also works for non-storyboard animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc04-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0fc04-127">See also</span></span>

- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [<span data-ttu-id="0fc04-128">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="0fc04-128">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="0fc04-129">Visão geral das técnicas de animação da propriedade</span><span class="sxs-lookup"><span data-stu-id="0fc04-129">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
