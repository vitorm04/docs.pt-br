---
title: 'Como: Preencher uma forma com uma cor sólida'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
ms.openlocfilehash: 576042d9d8e7a7f77d5375b7dfafafdc63b3e824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601955"
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="f2ff0-102">Como: Preencher uma forma com uma cor sólida</span><span class="sxs-lookup"><span data-stu-id="f2ff0-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="f2ff0-103">Para preencher uma forma com uma cor sólida, crie uma <xref:System.Drawing.SolidBrush> do objeto e, em seguida, passá-lo <xref:System.Drawing.SolidBrush> objeto como um argumento para um dos métodos de preenchimento do <xref:System.Drawing.Graphics> classe.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="f2ff0-104">O exemplo a seguir mostra como preencher uma elipse com a cor vermelha.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2ff0-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f2ff0-105">Example</span></span>  
 <span data-ttu-id="f2ff0-106">No código a seguir, o <xref:System.Drawing.SolidBrush.%23ctor%2A> construtor aceita um <xref:System.Drawing.Color> objeto como seu único argumento.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="f2ff0-107">Os valores usados pelo <xref:System.Drawing.Color.FromArgb%2A> método representam os componentes alfabéticos, vermelhos, verdes e azuis da cor.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="f2ff0-108">Cada um desses valores deve estar no intervalo de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="f2ff0-109">O primeiro 255 indica que a cor é totalmente opaca e o segundo 255 indica que o componente vermelho é de intensidade total.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="f2ff0-110">Os dois zeros indicam que os componentes verde e azul têm uma intensidade igual a 0.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="f2ff0-111">Os quatro números (0, 0, 100, 60) passados para o <xref:System.Drawing.Graphics.FillEllipse%2A> método especificar o local e o tamanho do retângulo delimitador para a elipse.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="f2ff0-112">O retângulo tem um canto superior esquerdo de (0, 0), uma largura de 100 e uma altura de 60.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f2ff0-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f2ff0-113">Compiling the Code</span></span>  
 <span data-ttu-id="f2ff0-114">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="f2ff0-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ff0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2ff0-115">See also</span></span>
- [<span data-ttu-id="f2ff0-116">Usando um pincel para preencher formas</span><span class="sxs-lookup"><span data-stu-id="f2ff0-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
