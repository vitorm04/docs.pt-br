---
title: Como criar texto com uma sombra
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], shadow effects
- shadow effects in text [WPF]
- text [WPF], shadowed
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
ms.openlocfilehash: c3e8135372ce4a092552c812cd971cb70bc49bf3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186843"
---
# <a name="how-to-create-text-with-a-shadow"></a><span data-ttu-id="d2687-102">Como criar texto com uma sombra</span><span class="sxs-lookup"><span data-stu-id="d2687-102">How to: Create Text with a Shadow</span></span>
<span data-ttu-id="d2687-103">Os exemplos nesta seção mostram como criar um efeito de sombra para texto exibido.</span><span class="sxs-lookup"><span data-stu-id="d2687-103">The examples in this section show how to create a shadow effect for displayed text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2687-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d2687-104">Example</span></span>  
 <span data-ttu-id="d2687-105">O <xref:System.Windows.Media.Effects.DropShadowEffect> objeto permite criar uma variedade de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] efeitos de sombra projetada para objetos.</span><span class="sxs-lookup"><span data-stu-id="d2687-105">The <xref:System.Windows.Media.Effects.DropShadowEffect> object allows you to create a variety of drop shadow effects for [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] objects.</span></span> <span data-ttu-id="d2687-106">O exemplo a seguir mostra um efeito de sombra aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-106">The following example shows a drop shadow effect applied to text.</span></span> <span data-ttu-id="d2687-107">Nesse caso, a sombra é suave, o que significa que a cor da sombra é desfocada.</span><span class="sxs-lookup"><span data-stu-id="d2687-107">In this case, the shadow is a soft shadow, which means the shadow color blurs.</span></span>  
  
 ![Sombra de texto com Maciez &#61; 0,25](./media/how-to-create-text-with-a-shadow/drop-shadow-text-effect.jpg)
  
 <span data-ttu-id="d2687-109">Você pode controlar a largura de <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> uma sombra definindo a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2687-109">You can control the width of a shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> property.</span></span> <span data-ttu-id="d2687-110">Um valor `4.0` de indica uma largura de sombra de 4 pixels.</span><span class="sxs-lookup"><span data-stu-id="d2687-110">A value of `4.0` indicates a shadow width of 4 pixels.</span></span> <span data-ttu-id="d2687-111">Você pode controlar a maciez, ou borrar, de uma sombra modificando a <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2687-111">You can control the softness, or blur, of a shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property.</span></span> <span data-ttu-id="d2687-112">Um valor `0.0` de não indica embaçamento.</span><span class="sxs-lookup"><span data-stu-id="d2687-112">A value of `0.0` indicates no blurring.</span></span> <span data-ttu-id="d2687-113">O exemplo de código a seguir mostra como criar uma sombra suave.</span><span class="sxs-lookup"><span data-stu-id="d2687-113">The following code example shows how to create a soft shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
> <span data-ttu-id="d2687-114">Esses efeitos de sombra [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] não passam pelo pipeline de renderização de texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-114">These shadow effects do not go through the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] text rendering pipeline.</span></span> <span data-ttu-id="d2687-115">Como resultado, ClearType fica desabilitado ao usar esses efeitos.</span><span class="sxs-lookup"><span data-stu-id="d2687-115">As a result, ClearType is disabled when using these effects.</span></span>  
  
 <span data-ttu-id="d2687-116">O exemplo a seguir mostra um efeito de sombra sólida aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-116">The following example shows a hard drop shadow effect applied to text.</span></span> <span data-ttu-id="d2687-117">Nesse caso, a sombra não está desfocada.</span><span class="sxs-lookup"><span data-stu-id="d2687-117">In this case, the shadow is not blurred.</span></span>  
  
 ![Sombra de texto com Maciez &#61; 0](./media/how-to-create-text-with-a-shadow/text-shadow-softness.jpg)
  
 <span data-ttu-id="d2687-119">Você pode criar uma sombra <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> dura `0.0`definindo a propriedade para , o que indica que nenhum borrão é usado.</span><span class="sxs-lookup"><span data-stu-id="d2687-119">You can create a hard shadow by setting the <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> property to `0.0`, which indicates that no blurring is used.</span></span> <span data-ttu-id="d2687-120">Você pode controlar a direção da <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> sombra modificando a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2687-120">You can control the direction of the shadow by modifying the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property.</span></span> <span data-ttu-id="d2687-121">Defina o valor direcional desta `0` propriedade `360`em um grau entre e .</span><span class="sxs-lookup"><span data-stu-id="d2687-121">Set the directional value of this property to a degree between `0` and `360`.</span></span> <span data-ttu-id="d2687-122">A ilustração a seguir mostra <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> os valores direcionais da configuração da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d2687-122">The following illustration shows the directional values of the <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> property setting.</span></span>  
  
 ![Configuração de grau de sombra de DropShadow](./media/how-to-create-text-with-a-shadow/drop-shadow-degree-setting.png)
  
 <span data-ttu-id="d2687-124">O exemplo de código a seguir mostra como criar uma sombra sólida.</span><span class="sxs-lookup"><span data-stu-id="d2687-124">The following code example shows how to create a hard shadow.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## <a name="using-a-blur-effect"></a><span data-ttu-id="d2687-125">Usando um efeito de desfoque</span><span class="sxs-lookup"><span data-stu-id="d2687-125">Using a Blur Effect</span></span>  
 <span data-ttu-id="d2687-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> pode ser usado para criar um efeito semelhante à sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-126">A <xref:System.Windows.Media.Effects.BlurBitmapEffect> can be used to create a shadow-like effect that can be placed behind a text object.</span></span> <span data-ttu-id="d2687-127">Um efeito de bitmap de desfoque aplicado ao texto desfoca o texto uniformemente em todas as direções.</span><span class="sxs-lookup"><span data-stu-id="d2687-127">A blur bitmap effect applied to text blurs the text evenly in all directions.</span></span>  
  
 <span data-ttu-id="d2687-128">O exemplo a seguir mostra um efeito de desfoque aplicado ao texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-128">The following example shows a blur effect applied to text.</span></span>  
  
 ![Sombra de texto usando BlurBitmapEffect](./media/how-to-create-text-with-a-shadow/text-shadow-blur-effect.jpg)  
  
 <span data-ttu-id="d2687-130">O exemplo de código a seguir mostra como criar um efeito de desfoque.</span><span class="sxs-lookup"><span data-stu-id="d2687-130">The following code example shows how to create a blur effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet6](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## <a name="using-a-translate-transform"></a><span data-ttu-id="d2687-131">Usando uma transformação de movimentação</span><span class="sxs-lookup"><span data-stu-id="d2687-131">Using a Translate Transform</span></span>  
 <span data-ttu-id="d2687-132">A <xref:System.Windows.Media.TranslateTransform> pode ser usado para criar um efeito semelhante à sombra que pode ser colocado atrás de um objeto de texto.</span><span class="sxs-lookup"><span data-stu-id="d2687-132">A <xref:System.Windows.Media.TranslateTransform> can be used to create a shadow-like effect that can be placed behind a text object.</span></span>  
  
 <span data-ttu-id="d2687-133">O exemplo de <xref:System.Windows.Media.TranslateTransform> código a seguir usa um texto para compensar.</span><span class="sxs-lookup"><span data-stu-id="d2687-133">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="d2687-134">Neste exemplo, uma cópia ligeiramente deslocada de texto abaixo do texto primário cria um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="d2687-134">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 ![Sombra de texto usando TranslateTransform](./media/how-to-create-text-with-a-shadow/text-transform-shadow-effect.jpg)
  
 <span data-ttu-id="d2687-136">O exemplo de código a seguir mostra como criar uma transformação para um efeito de sombra.</span><span class="sxs-lookup"><span data-stu-id="d2687-136">The following code example shows how to create a transform for a shadow effect.</span></span>  
  
 [!code-xaml[TextShadowSnippets#TextShadowSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]
