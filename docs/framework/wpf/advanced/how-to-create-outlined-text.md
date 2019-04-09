---
title: 'Como: Criar texto contornado'
ms.date: 03/30/2017
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
ms.openlocfilehash: 237bdc097cd2a3fbfff6dd79bce401c2d091e211
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162222"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="9deb7-102">Como: Criar texto contornado</span><span class="sxs-lookup"><span data-stu-id="9deb7-102">How to: Create Outlined Text</span></span>
<span data-ttu-id="9deb7-103">Na maioria dos casos, ao adicionar ornamentos a cadeias de caracteres de texto em seu aplicativo [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], você está usando texto em termos de uma coleção de caracteres separados ou glifos.</span><span class="sxs-lookup"><span data-stu-id="9deb7-103">In most cases, when you are adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="9deb7-104">Por exemplo, você poderia criar um pincel de gradiente linear e aplicá-lo para o <xref:System.Windows.Controls.Control.Foreground%2A> propriedade de um <xref:System.Windows.Controls.TextBox> objeto.</span><span class="sxs-lookup"><span data-stu-id="9deb7-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="9deb7-105">Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="9deb7-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Texto exibido com um pincel de gradiente linear](./media/how-to-create-outlined-text/text-linear-gradient.jpg)    
  
 <span data-ttu-id="9deb7-107">No entanto, você também pode converter texto em <xref:System.Windows.Media.Geometry> objetos, permitindo que você crie outros tipos de texto visualmente atrativo.</span><span class="sxs-lookup"><span data-stu-id="9deb7-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="9deb7-108">Por exemplo, você pode criar um <xref:System.Windows.Media.Geometry> objeto com base no contorno de uma cadeia de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="9deb7-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="9deb7-110">Quando o texto é convertido em um <xref:System.Windows.Media.Geometry> do objeto, ele não é mais um conjunto de caracteres — você não pode modificar os caracteres na cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="9deb7-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="9deb7-111">No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento.</span><span class="sxs-lookup"><span data-stu-id="9deb7-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="9deb7-112">O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="9deb7-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="9deb7-113">Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="9deb7-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="9deb7-116">Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="9deb7-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="9deb7-117">O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traço e realce do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="9deb7-117">The following example illustrates a way to creating visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Texto com pincel de imagem aplicado para traçar e realce](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="9deb7-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9deb7-119">Example</span></span>  
 <span data-ttu-id="9deb7-120">A chave para converter texto em uma <xref:System.Windows.Media.Geometry> objeto é usar o <xref:System.Windows.Media.FormattedText> objeto.</span><span class="sxs-lookup"><span data-stu-id="9deb7-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="9deb7-121">Depois de criar esse objeto, você pode usar o <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> e <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> métodos para converter o texto a ser <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="9deb7-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="9deb7-122">O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado.</span><span class="sxs-lookup"><span data-stu-id="9deb7-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="9deb7-123">O exemplo de código a seguir mostra como criar um <xref:System.Windows.Media.FormattedText> objeto e recuperar as geometrias do texto formatado e da caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="9deb7-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="9deb7-124">Para exibir o recuperado o <xref:System.Windows.Media.Geometry> objetos, você precisa acessar o <xref:System.Windows.Media.DrawingContext> do objeto que está exibindo o texto convertido.</span><span class="sxs-lookup"><span data-stu-id="9deb7-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that is displaying the converted text.</span></span> <span data-ttu-id="9deb7-125">Nesses exemplos de código, isso é feito criando um objeto de controle personalizado derivado de uma classe que dá suporte a renderização definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="9deb7-125">In these code examples, this is done by creating a custom control object that is derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="9deb7-126">Para exibir <xref:System.Windows.Media.Geometry> objetos no controle personalizado, forneça uma substituição para o <xref:System.Windows.UIElement.OnRender%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9deb7-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="9deb7-127">O método substituído deve usar o <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> método para desenhar o <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="9deb7-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="9deb7-128">Para a fonte do objeto de controle de usuário personalizada de exemplo, consulte [OutlineTextControl.cs para C# ](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) e [OutlineTextControl.vb para o Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="9deb7-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/samples/blob/master/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/samples/blob/master/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="9deb7-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9deb7-129">See also</span></span>

- [<span data-ttu-id="9deb7-130">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="9deb7-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
