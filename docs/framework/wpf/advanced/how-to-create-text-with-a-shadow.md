---
title: 'Como: Criar texto com uma sombra'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: a2225e297dbc0b5f9d49799cb34eb5539746e62e
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125779"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="d9f6a-102">Como: Criar texto com uma sombra</span><span class="sxs-lookup"><span data-stu-id="d9f6a-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="d9f6a-103">Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9f6a-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9f6a-104">Example</span></span>  
 <span data-ttu-id="d9f6a-105">O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite que você crie uma variedade de efeitos de sombra para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="d9f6a-106">O exemplo a seguir mostra um efeito de sombra aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="d9f6a-107">Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Sombra de texto com Suavidade &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg) 
  
 <span data-ttu-id="d9f6a-109">Você pode controlar a largura de uma sombra definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="d9f6a-110">Um valor de `4.0` indica uma sombra de 4 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="d9f6a-111">Você pode controlar a suavidade, ou de uma sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="d9f6a-112">Um valor de `0.0` não indica nenhum desfoque.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="d9f6a-113">O exemplo de código a seguir mostra como criar uma sombra suave.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="d9f6a-114">Esses efeitos de sombra não passam pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pipeline de renderização de texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="d9f6a-115">Como resultado, ClearType fica desabilitado ao usar esses efeitos.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="d9f6a-116">O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="d9f6a-117">Nesse caso, a sombra não está desfocada.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Sombra de texto com Suavidade &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg) 
  
 <span data-ttu-id="d9f6a-119">Você pode criar uma sombra sólida definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade para `0.0`, que indica que nenhum desfoque é utilizado.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="d9f6a-120">Você pode controlar a direção da sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="d9f6a-121">Defina o valor direcional desta propriedade como um grau entre `0` e `360`.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="d9f6a-122">A ilustração a seguir mostra os valores direcionais do <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> configuração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Configuração de grau de DropShadow através de sombra](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="d9f6a-124">O exemplo de código a seguir mostra como criar uma sombra sólida.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="d9f6a-125">Usando um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="d9f6a-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="d9f6a-126">Um <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="d9f6a-127">Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="d9f6a-128">O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Sombra de texto usando BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="d9f6a-130">O exemplo de código a seguir mostra como criar um efeito de desfoque.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="d9f6a-131">Usando uma transformação de movimentação</span><span class="sxs-lookup"><span data-stu-id="d9f6a-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="d9f6a-132">Um <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="d9f6a-133">O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar o texto.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="d9f6a-134">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Sombra de texto usando TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)    
  
 <span data-ttu-id="d9f6a-136">O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="d9f6a-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
