---
title: Como criar texto com uma sombra
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bbc3da54c10304e52f93d38365a8d9ed005505
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="fe970-102">Como criar texto com uma sombra</span><span class="sxs-lookup"><span data-stu-id="fe970-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="fe970-103">Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.</span><span class="sxs-lookup"><span data-stu-id="fe970-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe970-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe970-104">Example</span></span>  
 <span data-ttu-id="fe970-105">O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite que você crie uma variedade de efeitos de sombra para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="fe970-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="fe970-106">O exemplo a seguir mostra um efeito de sombra aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="fe970-107">Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.</span><span class="sxs-lookup"><span data-stu-id="fe970-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="fe970-108">![Sombra de texto com Suavidade &#61; 0,25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="fe970-108">![Text shadow with Softness &#61; 0.25](../../../../docs/framework/wpf/advanced/media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="fe970-109">Exemplo de texto com uma sombra suave</span><span class="sxs-lookup"><span data-stu-id="fe970-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="fe970-110">Você pode controlar a largura de uma sombra definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe970-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="fe970-111">Um valor de `4.0` indica uma sombra de 4 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="fe970-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="fe970-112">Você pode controlar a suavidade de uma sombra modificando o <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe970-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="fe970-113">Um valor de `0.0` não indica nenhum obscurecendo.</span><span class="sxs-lookup"><span data-stu-id="fe970-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="fe970-114">O exemplo de código a seguir mostra como criar uma sombra suave.</span><span class="sxs-lookup"><span data-stu-id="fe970-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="fe970-115">Esses efeitos de sombra não vão para o [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pipeline de processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="fe970-116">Como resultado, ClearType fica desabilitado ao usar esses efeitos.</span><span class="sxs-lookup"><span data-stu-id="fe970-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="fe970-117">O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="fe970-118">Nesse caso, a sombra não está desfocada.</span><span class="sxs-lookup"><span data-stu-id="fe970-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="fe970-119">![Sombra de texto com Suavidade &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="fe970-119">![Text shadow with Softness &#61; 0](../../../../docs/framework/wpf/advanced/media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="fe970-120">Exemplo de texto com uma sombra sólida</span><span class="sxs-lookup"><span data-stu-id="fe970-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="fe970-121">Você pode criar uma sombra sólida definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade `0.0`, indicando que nenhum obscurecendo é usada.</span><span class="sxs-lookup"><span data-stu-id="fe970-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="fe970-122">Você pode controlar a direção da sombra modificando o <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe970-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="fe970-123">Defina o valor direcional desta propriedade como um grau entre `0` e `360`.</span><span class="sxs-lookup"><span data-stu-id="fe970-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="fe970-124">A ilustração a seguir mostra os valores direcionais do <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> configuração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="fe970-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="fe970-125">![Configuração de grau de sombra da sombra](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="fe970-125">![DropShadow degree setting of shadow](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="fe970-126">Diagrama de direção de DropShadow</span><span class="sxs-lookup"><span data-stu-id="fe970-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="fe970-127">O exemplo de código a seguir mostra como criar uma sombra sólida.</span><span class="sxs-lookup"><span data-stu-id="fe970-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="fe970-128">Usando um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="fe970-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="fe970-129">Um <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado por trás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="fe970-130">Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="fe970-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="fe970-131">O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="fe970-132">![Sombra de texto usando BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="fe970-132">![Text shadow using a BlurBitmapEffect](../../../../docs/framework/wpf/advanced/media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="fe970-133">Exemplo de texto com um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="fe970-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="fe970-134">O exemplo de código a seguir mostra como criar um efeito de desfoque.</span><span class="sxs-lookup"><span data-stu-id="fe970-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="fe970-135">Usando uma transformação de movimentação</span><span class="sxs-lookup"><span data-stu-id="fe970-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="fe970-136">Um <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado por trás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="fe970-137">O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar texto.</span><span class="sxs-lookup"><span data-stu-id="fe970-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="fe970-138">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="fe970-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="fe970-139">![Sombra de texto usando TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="fe970-139">![Text shadow using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="fe970-140">Exemplo de texto usando uma transformação para efeito de sombra</span><span class="sxs-lookup"><span data-stu-id="fe970-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="fe970-141">O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="fe970-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
