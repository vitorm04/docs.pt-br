---
title: Como criar texto de estrutura de tópicos
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
ms.openlocfilehash: 86bfa396a2aa44eb511c014687501d60e170a396
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278919"
---
# <a name="how-to-create-outlined-text"></a><span data-ttu-id="dc118-102">Como: Criar texto delineado</span><span class="sxs-lookup"><span data-stu-id="dc118-102">How to: Create outlined text</span></span>

<span data-ttu-id="dc118-103">Na maioria dos casos, quando você está adicionando [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ornamentação a strings de texto em sua aplicação, você está usando texto em termos de uma coleção de caracteres discretos, ou glifos.</span><span class="sxs-lookup"><span data-stu-id="dc118-103">In most cases, when you're adding ornamentation to text strings in your [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] application, you are using text in terms of a collection of discrete characters, or glyphs.</span></span> <span data-ttu-id="dc118-104">Por exemplo, você pode criar um pincel de <xref:System.Windows.Controls.Control.Foreground%2A> gradiente <xref:System.Windows.Controls.TextBox> linear e aplicá-lo à propriedade de um objeto.</span><span class="sxs-lookup"><span data-stu-id="dc118-104">For example, you could create a linear gradient brush and apply it to the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.TextBox> object.</span></span> <span data-ttu-id="dc118-105">Ao exibir ou editar a caixa de texto, o pincel de gradiente linear é aplicado automaticamente ao conjunto de caracteres atual na cadeia de texto.</span><span class="sxs-lookup"><span data-stu-id="dc118-105">When you display or edit the text box, the linear gradient brush is automatically applied to the current set of characters in the text string.</span></span>  
  
 ![Texto exibido com um pincel de gradiente linear](./media/how-to-create-outlined-text/text-linear-gradient.jpg)
  
 <span data-ttu-id="dc118-107">No entanto, você <xref:System.Windows.Media.Geometry> também pode converter texto em objetos, permitindo que você crie outros tipos de texto visualmente rico.</span><span class="sxs-lookup"><span data-stu-id="dc118-107">However, you can also convert text into <xref:System.Windows.Media.Geometry> objects, allowing you to create other types of visually rich text.</span></span> <span data-ttu-id="dc118-108">Por exemplo, você <xref:System.Windows.Media.Geometry> pode criar um objeto com base no contorno de uma seqüência de texto.</span><span class="sxs-lookup"><span data-stu-id="dc118-108">For example, you could create a <xref:System.Windows.Media.Geometry> object based on the outline of a text string.</span></span>  
  
 ![Contorno do texto usando um pincel de gradiente linear](./media/how-to-create-outlined-text/text-outline-linear-gradient.jpg)  
  
 <span data-ttu-id="dc118-110">Quando o texto é <xref:System.Windows.Media.Geometry> convertido em um objeto, ele não é mais uma coleção de caracteres — você não pode modificar os caracteres na seqüência de texto.</span><span class="sxs-lookup"><span data-stu-id="dc118-110">When text is converted to a <xref:System.Windows.Media.Geometry> object, it is no longer a collection of characters—you cannot modify the characters in the text string.</span></span> <span data-ttu-id="dc118-111">No entanto, é possível afetar a aparência do texto convertido modificando suas propriedades de traço e preenchimento.</span><span class="sxs-lookup"><span data-stu-id="dc118-111">However, you can affect the appearance of the converted text by modifying its stroke and fill properties.</span></span> <span data-ttu-id="dc118-112">O traço refere-se ao contorno do texto convertido; o preenchimento refere-se à área dentro do contorno do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="dc118-112">The stroke refers to the outline of the converted text; the fill refers to the area inside the outline of the converted text.</span></span>  
  
 <span data-ttu-id="dc118-113">Os exemplos a seguir ilustram várias maneiras de criar efeitos visuais modificando o traço e o preenchimento do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="dc118-113">The following examples illustrate several ways of creating visual effects by modifying the stroke and fill of converted text.</span></span>  
  
 ![Texto com diferentes cores de preenchimento e traço](./media/how-to-create-outlined-text/fill-stroke-text-effect.jpg)  
  
 ![Texto com pincel de imagem aplicado ao traço](./media/how-to-create-outlined-text/image-brush-application.jpg)
  
 <span data-ttu-id="dc118-116">Também é possível modificar o retângulo da caixa delimitadora ou realce, do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="dc118-116">It is also possible to modify the bounding box rectangle, or highlight, of the converted text.</span></span> <span data-ttu-id="dc118-117">O exemplo a seguir ilustra uma maneira de criar efeitos visuais modificando o traçado e o destaque do texto convertido.</span><span class="sxs-lookup"><span data-stu-id="dc118-117">The following example illustrates a way to create visual effects by modifying the stroke and highlight of converted text.</span></span>  
  
 ![Texto com pincel de imagem aplicado ao traçado e destaque](./media/how-to-create-outlined-text/image-brush-text-application.jpg)

## <a name="example"></a><span data-ttu-id="dc118-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dc118-119">Example</span></span>  
 <span data-ttu-id="dc118-120">A chave para converter <xref:System.Windows.Media.Geometry> texto em um <xref:System.Windows.Media.FormattedText> objeto é usar o objeto.</span><span class="sxs-lookup"><span data-stu-id="dc118-120">The key to converting text to a <xref:System.Windows.Media.Geometry> object is to use the <xref:System.Windows.Media.FormattedText> object.</span></span> <span data-ttu-id="dc118-121">Depois de criar esse objeto, você <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> pode usar os métodos e métodos para converter o texto em <xref:System.Windows.Media.Geometry> objetos.</span><span class="sxs-lookup"><span data-stu-id="dc118-121">Once you have created this object, you can use the <xref:System.Windows.Media.FormattedText.BuildGeometry%2A> and <xref:System.Windows.Media.FormattedText.BuildHighlightGeometry%2A> methods to convert the text to <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="dc118-122">O primeiro método retorna a geometria do texto formatado; o segundo método retorna a geometria da caixa delimitadora do texto formatado.</span><span class="sxs-lookup"><span data-stu-id="dc118-122">The first method returns the geometry of the formatted text; the second method returns the geometry of the formatted text's bounding box.</span></span> <span data-ttu-id="dc118-123">O exemplo de código a <xref:System.Windows.Media.FormattedText> seguir mostra como criar um objeto e recuperar as geometrias do texto formatado e sua caixa delimitadora.</span><span class="sxs-lookup"><span data-stu-id="dc118-123">The following code example shows how to create a <xref:System.Windows.Media.FormattedText> object and to retrieve the geometries of the formatted text and its bounding box.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#CreateText](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#createtext)]
 [!code-vb[OutlineTextControlViewer#CreateText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#createtext)]  
  
 <span data-ttu-id="dc118-124">Para exibir os <xref:System.Windows.Media.Geometry> objetos recuperados, você precisa <xref:System.Windows.Media.DrawingContext> acessar o objeto que está exibindo o texto convertido.</span><span class="sxs-lookup"><span data-stu-id="dc118-124">In order to display the retrieved the <xref:System.Windows.Media.Geometry> objects, you need to access the <xref:System.Windows.Media.DrawingContext> of the object that's displaying the converted text.</span></span> <span data-ttu-id="dc118-125">Nesses exemplos de código, esse acesso é obtido criando um objeto de controle personalizado derivado de uma classe que suporta renderização definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="dc118-125">In these code examples, this access is achieved by creating a custom control object that's derived from a class that supports user-defined rendering.</span></span>  
  
 <span data-ttu-id="dc118-126">Para <xref:System.Windows.Media.Geometry> exibir objetos no controle personalizado, <xref:System.Windows.UIElement.OnRender%2A> forneça uma substituição para o método.</span><span class="sxs-lookup"><span data-stu-id="dc118-126">To display <xref:System.Windows.Media.Geometry> objects in the custom control, provide an override for the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span> <span data-ttu-id="dc118-127">Seu método substituído deve <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> usar o <xref:System.Windows.Media.Geometry> método para desenhar os objetos.</span><span class="sxs-lookup"><span data-stu-id="dc118-127">Your overridden method should use the <xref:System.Windows.Media.DrawingContext.DrawGeometry%2A> method to draw the <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
 [!code-csharp[OutlineTextControlViewer#OnRender](~/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs#onrender)]
 [!code-vb[OutlineTextControlViewer#OnRender](~/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb#onrender)]  
  
  <span data-ttu-id="dc118-128">Para obter a origem do exemplo do objeto de controle personalizado do usuário, consulte [OutlineTextControl.cs para C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) e [OutlineTextControl.vb para Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span><span class="sxs-lookup"><span data-stu-id="dc118-128">For the source of the example custom user control object, see [OutlineTextControl.cs for C#](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/OutlineTextControlViewer/CSharp/OutlineTextControl.cs) and [OutlineTextControl.vb for Visual Basic](https://github.com/dotnet/docs/blob/master/samples/snippets/visualbasic/VS_Snippets_Wpf/OutlineTextControlViewer/visualbasic/outlinetextcontrol.vb).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc118-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="dc118-129">See also</span></span>

- [<span data-ttu-id="dc118-130">Desenhando texto formatado</span><span class="sxs-lookup"><span data-stu-id="dc118-130">Drawing Formatted Text</span></span>](drawing-formatted-text.md)
