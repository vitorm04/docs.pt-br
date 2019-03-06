---
title: 'Como: Criar texto com uma sombra'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: 4d200aa980e8f2e6d22291669dfb07db54a5f0c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370664"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="9f407-102">Como: Criar texto com uma sombra</span><span class="sxs-lookup"><span data-stu-id="9f407-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="9f407-103">Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.</span><span class="sxs-lookup"><span data-stu-id="9f407-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f407-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f407-104">Example</span></span>  
 <span data-ttu-id="9f407-105">O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite que você crie uma variedade de efeitos de sombra para [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="9f407-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="9f407-106">O exemplo a seguir mostra um efeito de sombra aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="9f407-107">Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.</span><span class="sxs-lookup"><span data-stu-id="9f407-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 <span data-ttu-id="9f407-108">![Sombra de texto com Suavidade &#61; 0,25](./media/shadowtext01.jpg "ShadowText01")</span><span class="sxs-lookup"><span data-stu-id="9f407-108">![Text shadow with Softness &#61; 0.25](./media/shadowtext01.jpg "ShadowText01")</span></span>  
<span data-ttu-id="9f407-109">Exemplo de texto com uma sombra suave</span><span class="sxs-lookup"><span data-stu-id="9f407-109">Example of text with a soft shadow</span></span>  
  
 <span data-ttu-id="9f407-110">Você pode controlar a largura de uma sombra definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f407-110">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="9f407-111">Um valor de `4.0` indica uma sombra de 4 pixels de largura.</span><span class="sxs-lookup"><span data-stu-id="9f407-111">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="9f407-112">Você pode controlar a suavidade, ou de uma sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f407-112">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="9f407-113">Um valor de `0.0` não indica nenhum desfoque.</span><span class="sxs-lookup"><span data-stu-id="9f407-113">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="9f407-114">O exemplo de código a seguir mostra como criar uma sombra suave.</span><span class="sxs-lookup"><span data-stu-id="9f407-114">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  <span data-ttu-id="9f407-115">Esses efeitos de sombra não passam pelo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pipeline de renderização de texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-115">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="9f407-116">Como resultado, ClearType fica desabilitado ao usar esses efeitos.</span><span class="sxs-lookup"><span data-stu-id="9f407-116">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="9f407-117">O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-117">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="9f407-118">Nesse caso, a sombra não está desfocada.</span><span class="sxs-lookup"><span data-stu-id="9f407-118">In this case, the shadow is not blurred.</span></span>  
  
 <span data-ttu-id="9f407-119">![Sombra de texto com Suavidade &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span><span class="sxs-lookup"><span data-stu-id="9f407-119">![Text shadow with Softness &#61; 0](./media/shadowtext02.jpg "ShadowText02")</span></span>  
<span data-ttu-id="9f407-120">Exemplo de texto com uma sombra sólida</span><span class="sxs-lookup"><span data-stu-id="9f407-120">Example of text with a hard shadow</span></span>  
  
 <span data-ttu-id="9f407-121">Você pode criar uma sombra sólida definindo a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade para `0.0`, que indica que nenhum desfoque é utilizado.</span><span class="sxs-lookup"><span data-stu-id="9f407-121">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="9f407-122">Você pode controlar a direção da sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f407-122">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="9f407-123">Defina o valor direcional desta propriedade como um grau entre `0` e `360`.</span><span class="sxs-lookup"><span data-stu-id="9f407-123">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="9f407-124">A ilustração a seguir mostra os valores direcionais do <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> configuração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="9f407-124">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 <span data-ttu-id="9f407-125">![Configuração de grau de DropShadow através de sombra](./media/shadowtext08.png "ShadowText08")</span><span class="sxs-lookup"><span data-stu-id="9f407-125">![DropShadow degree setting of shadow](./media/shadowtext08.png "ShadowText08")</span></span>  
<span data-ttu-id="9f407-126">Diagrama de direção de DropShadow</span><span class="sxs-lookup"><span data-stu-id="9f407-126">DropShadow Direction diagram</span></span>  
  
 <span data-ttu-id="9f407-127">O exemplo de código a seguir mostra como criar uma sombra sólida.</span><span class="sxs-lookup"><span data-stu-id="9f407-127">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="9f407-128">Usando um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="9f407-128">Using a Blur Effect</span></span>  
 <span data-ttu-id="9f407-129">Um <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-129">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="9f407-130">Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="9f407-130">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="9f407-131">O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-131">The following example shows a blur effect applied to text.</span></span>  
  
 <span data-ttu-id="9f407-132">![Sombra de texto usando BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span><span class="sxs-lookup"><span data-stu-id="9f407-132">![Text shadow using a BlurBitmapEffect](./media/shadowtext06.jpg "ShadowText06")</span></span>  
<span data-ttu-id="9f407-133">Exemplo de texto com um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="9f407-133">Example of text with a blur effect</span></span>  
  
 <span data-ttu-id="9f407-134">O exemplo de código a seguir mostra como criar um efeito de desfoque.</span><span class="sxs-lookup"><span data-stu-id="9f407-134">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="9f407-135">Usando uma transformação de movimentação</span><span class="sxs-lookup"><span data-stu-id="9f407-135">Using a Translate Transform</span></span>  
 <span data-ttu-id="9f407-136">Um <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante a sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-136">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="9f407-137">O seguinte exemplo de código usa um <xref:System.Windows.Media.TranslateTransform> para deslocar o texto.</span><span class="sxs-lookup"><span data-stu-id="9f407-137">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="9f407-138">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="9f407-138">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 <span data-ttu-id="9f407-139">![Sombra de texto usando TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span><span class="sxs-lookup"><span data-stu-id="9f407-139">![Text shadow using a TranslateTransform](./media/shadowtext07.jpg "ShadowText07")</span></span>  
<span data-ttu-id="9f407-140">Exemplo de texto usando uma transformação para efeito de sombra</span><span class="sxs-lookup"><span data-stu-id="9f407-140">Example of text using a transform for a shadow effect</span></span>  
  
 <span data-ttu-id="9f407-141">O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="9f407-141">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
