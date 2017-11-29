---
title: "Instruções passo a passo: criar um botão animado personalizado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom animated buttons [WPF]
- buttons [WPF]
- animation [WPF], buttons [WPF]
ms.assetid: e9532c72-460f-4898-9332-613fa21d746a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bce1140ed11332b5bf30d487b2acacc644687d26
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="walkthroughs-create-a-custom-animated-button"></a><span data-ttu-id="8f392-102">Instruções passo a passo: criar um botão animado personalizado</span><span class="sxs-lookup"><span data-stu-id="8f392-102">Walkthroughs: Create a Custom Animated Button</span></span>
<span data-ttu-id="8f392-103">Como o nome sugere, o [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] é excelente para fazer experiências avançadas de apresentação para clientes.</span><span class="sxs-lookup"><span data-stu-id="8f392-103">As its name suggests, [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] is great for making rich presentation experiences for customers.</span></span> <span data-ttu-id="8f392-104">Essas instruções passo a passo mostram como personalizar a aparência e o comportamento de um botão (incluindo animações).</span><span class="sxs-lookup"><span data-stu-id="8f392-104">These walkthroughs show you how to customize the look and behavior of a button (including animations).</span></span> <span data-ttu-id="8f392-105">Essa personalização é feita usando um estilo e modelo para que você possa aplicar esse botão personalizado facilmente aos botões em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8f392-105">This customization is done using a style and template so that you can apply this custom button easily to any buttons in your application.</span></span> <span data-ttu-id="8f392-106">A ilustração a seguir mostra o botão personalizado que você criará.</span><span class="sxs-lookup"><span data-stu-id="8f392-106">The following illustration shows the customized button that you will create.</span></span>  
  
 <span data-ttu-id="8f392-107">![O botão personalizado que você criará](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span><span class="sxs-lookup"><span data-stu-id="8f392-107">![The customized button that you will create](../../../../docs/framework/wpf/controls/media/custom-button-blend-intro.jpg "custom_button_blend_Intro")</span></span>  
  
 <span data-ttu-id="8f392-108">Os gráficos vetoriais que compõem a aparência do botão são criados usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f392-108">The vector graphics that make up the appearance of the button are created by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]<span data-ttu-id="8f392-109"> é semelhante ao HTML, exceto que ele é mais poderoso e extensível.</span><span class="sxs-lookup"><span data-stu-id="8f392-109"> is similar to HTML except it is more powerful and extensible.</span></span> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]<span data-ttu-id="8f392-110"> pode ser digitado manualmente usando o Microsoft Visual Studio ou o Bloco de notas, ou você pode usar uma ferramenta de design visual como o Microsoft Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8f392-110"> can be typed in manually using Microsoft Visual Studio or Notepad, or you can use a visual design tool such as Microsoft Expression Blend.</span></span> <span data-ttu-id="8f392-111">O Expression Blend funciona criando código [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] subjacente, para que ambos os métodos criem o mesmo gráfico.</span><span class="sxs-lookup"><span data-stu-id="8f392-111">Expression Blend works by creating underlying [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] code, so both methods create the same graphics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8f392-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8f392-112">In This Section</span></span>  
 [<span data-ttu-id="8f392-113">Criar um botão usando o Microsoft Expression Blend</span><span class="sxs-lookup"><span data-stu-id="8f392-113">Create a Button by Using Microsoft Expression Blend</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-microsoft-expression-blend.md)  
 <span data-ttu-id="8f392-114">Demonstra como criar botões com comportamento personalizado usando os recursos de designer do Expression Blend.</span><span class="sxs-lookup"><span data-stu-id="8f392-114">Demonstrates how to create buttons with custom behavior by using the designer features of Expression Blend.</span></span>  
  
 [<span data-ttu-id="8f392-115">Criar um botão usando XAML</span><span class="sxs-lookup"><span data-stu-id="8f392-115">Create a Button by Using XAML</span></span>](../../../../docs/framework/wpf/controls/walkthrough-create-a-button-by-using-xaml.md)  
 <span data-ttu-id="8f392-116">Demonstra como criar botões com comportamento personalizado usando [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] e [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8f392-116">Demonstrates how to create buttons with custom behavior by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] and [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8f392-117">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8f392-117">Related Sections</span></span>  
 [<span data-ttu-id="8f392-118">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="8f392-118">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 <span data-ttu-id="8f392-119">Descreve como os estilos e modelos podem ser usados para determinar a aparência e o comportamento dos controles.</span><span class="sxs-lookup"><span data-stu-id="8f392-119">Describes how styles and templates can be used to determine the appearance and behavior of controls.</span></span>  
  
 [<span data-ttu-id="8f392-120">Visão geral da animação</span><span class="sxs-lookup"><span data-stu-id="8f392-120">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 <span data-ttu-id="8f392-121">Descreve como os objetos podem ser animados usando a animação [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] e o sistema de temporização.</span><span class="sxs-lookup"><span data-stu-id="8f392-121">Describes how objects can be animated by using the [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] animation and timing system.</span></span>  
  
 [<span data-ttu-id="8f392-122">Visão geral da pintura com cores sólidas e gradientes</span><span class="sxs-lookup"><span data-stu-id="8f392-122">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 <span data-ttu-id="8f392-123">Descreve como usar objetos de pincel para pintar com cores sólidas, gradientes lineares e gradientes radiais.</span><span class="sxs-lookup"><span data-stu-id="8f392-123">Describes how to use brush objects to paint with solid colors, linear gradients, and radial gradients.</span></span>  
  
 [<span data-ttu-id="8f392-124">Visão geral dos efeitos de bitmap</span><span class="sxs-lookup"><span data-stu-id="8f392-124">Bitmap Effects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/bitmap-effects-overview.md)  
 <span data-ttu-id="8f392-125">Descreve os efeitos de bitmap aos quais o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dá suporte e explica como aplicá-los.</span><span class="sxs-lookup"><span data-stu-id="8f392-125">Describes the bitmap effects supported by [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] and explains how to apply them.</span></span>
