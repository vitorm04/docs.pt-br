---
title: "Como criar texto de estrutura de tópicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], linear gradient brush
- outlined text [WPF]
- gradient brush [WPF]
- linear gradient brush [WPF]
- typography [WPF], outline effects
ms.assetid: 4aa3cf6e-1953-4f26-8230-7c1409e5f28d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76d0dcf63f9d8a66106f4bcdc52a2bf98c75cdc4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="afe27-102">Como criar texto de estrutura de tópicos</span><span class="sxs-lookup"><span data-stu-id="afe27-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="afe27-103">Na maioria dos casos, ao adicionar ornamentos a cadeias de caracteres de texto em seu aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você está usando texto em termos de uma coleção de caracteres separados ou glifos.</span><span class="sxs-lookup"><span data-stu-id="afe27-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="afe27-104">Por exemplo, você pode criar um pincel de gradiente linear e aplicá-lo a <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.TextBox> objeto.</span><span class="sxs-lookup"><span data-stu-id="afe27-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="afe27-105">Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="afe27-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 <span data-ttu-id="afe27-106">![Texto exibido com um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span><span class="sxs-lookup"><span data-stu-id="afe27-106">![Text displayed with a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext01.jpg "OutlinedText01")</span></span>  
<span data-ttu-id="afe27-107">Exemplo de um pincel de gradiente linear aplicado a uma caixa de texto</span><span class="sxs-lookup"><span data-stu-id="afe27-107">Example of a linear gradient brush applied to a text box</span></span>  
  
 <span data-ttu-id="afe27-108">No entanto, você também pode converter texto em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de visualmente rich text.</span><span class="sxs-lookup"><span data-stu-id="afe27-108">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="afe27-109">Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="afe27-109">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 <span data-ttu-id="afe27-110">![Estrutura de tópicos de texto usando um pincel de gradiente linear](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span><span class="sxs-lookup"><span data-stu-id="afe27-110">![Text outline using a linear gradient brush](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")</span></span>  
<span data-ttu-id="afe27-111">Exemplo de um pincel de gradiente linear aplicado à geometria de contorno do texto</span><span class="sxs-lookup"><span data-stu-id="afe27-111">Example of a linear gradient brush applied to the outline geometry of text</span></span>  
  
 <span data-ttu-id="afe27-112">Quando o texto é convertido em um <xref:System.Windows.Media.Geometry> do objeto, ele não é mais um conjunto de caracteres — você não pode modificar os caracteres na cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="afe27-112">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="afe27-113">No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento.</span><span class="sxs-lookup"><span data-stu-id="afe27-113">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="afe27-114">O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="afe27-114">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="afe27-115">Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="afe27-115">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 <span data-ttu-id="afe27-116">![Texto com diferentes cores de preenchimento e traço](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span><span class="sxs-lookup"><span data-stu-id="afe27-116">![Text with different colors for fill and stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")</span></span>  
<span data-ttu-id="afe27-117">Exemplo de configuração de borda e preenchimento com diferentes cores.</span><span class="sxs-lookup"><span data-stu-id="afe27-117">Example of setting stroke and fill to different colors</span></span>  
  
 <span data-ttu-id="afe27-118">![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span><span class="sxs-lookup"><span data-stu-id="afe27-118">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")</span></span>  
<span data-ttu-id="afe27-119">Exemplo de um pincel de imagem aplicado ao traço</span><span class="sxs-lookup"><span data-stu-id="afe27-119">Example of an image brush applied to the stroke</span></span>  
  
 <span data-ttu-id="afe27-120">Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="afe27-120">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="afe27-121">O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traço e realce do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="afe27-121">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 <span data-ttu-id="afe27-122">![Texto com pincel de imagem aplicado ao traço](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span><span class="sxs-lookup"><span data-stu-id="afe27-122">![Text with image brush applied to stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")</span></span>  
<span data-ttu-id="afe27-123">Exemplo de um pincel de imagem aplicado ao traço e ao realce</span><span class="sxs-lookup"><span data-stu-id="afe27-123">Example of an image brush applied to the stroke and highlight</span></span>  
  
## <a name="example"></a><span data-ttu-id="afe27-124">Exemplo</span><span class="sxs-lookup"><span data-stu-id="afe27-124">Example</span></span>  
 <span data-ttu-id="afe27-125">A chave para converter texto em uma <xref:System.Windows.Media.Geometry> objeto é usar o <xref:System.Windows.Media.FormattedText> objeto.</span><span class="sxs-lookup"><span data-stu-id="afe27-125">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="afe27-126">Depois de criar esse objeto, você pode usar o <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> e <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> métodos para converter o texto a ser <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="afe27-126">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="afe27-127">O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado.</span><span class="sxs-lookup"><span data-stu-id="afe27-127">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="afe27-128">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> objeto e recuperar as geometrias do texto formatado e da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="afe27-128">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="afe27-129">Para exibir recuperada a <xref:System.Windows.Media.Geometry> objetos, você precisa acessar o <xref:System.Windows.Media.DrawingContext> do objeto que está exibindo o texto convertido.</span><span class="sxs-lookup"><span data-stu-id="afe27-129">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="afe27-130">Nesses exemplos de código, isso é feito criando um objeto de controle personalizado derivado de uma classe que dá suporte a renderização definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="afe27-130">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="afe27-131">Para exibir <xref:System.Windows.Media.Geometry> objetos no controle personalizado, fornecer uma substituição para o <xref:System.Windows.UIElement.OnRender%2A> método.</span><span class="sxs-lookup"><span data-stu-id="afe27-131">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="afe27-132">O método sobrescrito deve usar o <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> método para desenhar o <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="afe27-132">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](../../../../samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
## <a name="see-also"></a><span data-ttu-id="afe27-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="afe27-133">See Also</span></span>  
 [<span data-ttu-id="afe27-134">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="afe27-134">Drawing Formatted Text</span></span>](../../../../docs/framework/wpf/advanced/drawing-formatted-text.md)
