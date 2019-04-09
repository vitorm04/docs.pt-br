---
title: 'Como: desenhar uma linha em um formulário do Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Graphics.DrawLine
helpviewer_keywords:
- examples [Windows Forms], drawing lines on forms
- drawing [Windows Forms], lines
- lines [Windows Forms], drawing
- drawing lines
ms.assetid: 55c1dbeb-75d0-430c-9814-a24b8971ad8c
ms.openlocfilehash: aab04b9236175cedd154b817db5a6f6450503105
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074438"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="df4d6-102">Como: desenhar uma linha em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="df4d6-102">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="df4d6-103">Este exemplo desenha uma linha em um formulário.</span><span class="sxs-lookup"><span data-stu-id="df4d6-103">This example draws a line on a form.</span></span> <span data-ttu-id="df4d6-104">Normalmente, quando você desenha em um formulário, tratar do formulário <xref:System.Windows.Forms.Control.Paint> eventos e executar o desenho usando o <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> propriedade do <xref:System.Windows.Forms.PaintEventArgs>, conforme mostrado neste exemplo</span><span class="sxs-lookup"><span data-stu-id="df4d6-104">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="df4d6-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="df4d6-105">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="df4d6-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="df4d6-106">Compiling the Code</span></span>  
 <span data-ttu-id="df4d6-107">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs>`e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="df4d6-107">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="df4d6-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="df4d6-108">Robust Programming</span></span>  
 <span data-ttu-id="df4d6-109">Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> em todos os objetos que consomem recursos do sistema, tais como <xref:System.Drawing.Pen> objetos.</span><span class="sxs-lookup"><span data-stu-id="df4d6-109">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df4d6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df4d6-110">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="df4d6-111">Introdução à programação de elementos gráficos</span><span class="sxs-lookup"><span data-stu-id="df4d6-111">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="df4d6-112">Usando uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="df4d6-112">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="df4d6-113">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df4d6-113">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
