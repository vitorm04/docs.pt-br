---
title: Como desenhar uma linha em um formulário do Windows Forms
description: Saiba como desenhar uma linha em um formulário manipulando o evento de pintura e, em seguida, executar o desenho usando a Propriedade Graphics de PaintEventArgs.
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
ms.openlocfilehash: c8e92dc265c63413275561d0e2e3aa820eaec724
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621620"
---
# <a name="how-to-draw-a-line-on-a-windows-form"></a><span data-ttu-id="60ae6-103">Como desenhar uma linha em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60ae6-103">How to: Draw a Line on a Windows Form</span></span>
<span data-ttu-id="60ae6-104">Este exemplo desenha uma linha em um formulário.</span><span class="sxs-lookup"><span data-stu-id="60ae6-104">This example draws a line on a form.</span></span> <span data-ttu-id="60ae6-105">Normalmente, quando você desenha em um formulário, manipula o evento do formulário <xref:System.Windows.Forms.Control.Paint> e executa o desenho usando a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> Propriedade do <xref:System.Windows.Forms.PaintEventArgs> , conforme mostrado neste exemplo</span><span class="sxs-lookup"><span data-stu-id="60ae6-105">Typically, when you draw on a form, you handle the form’s  <xref:System.Windows.Forms.Control.Paint> event and perform the drawing using the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property of the <xref:System.Windows.Forms.PaintEventArgs>, as shown in this example</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ae6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60ae6-106">Example</span></span>  
 [!code-csharp[System.Drawing.UsingAPen#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="60ae6-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="60ae6-107">Compiling the Code</span></span>  
 <span data-ttu-id="60ae6-108">O exemplo anterior foi projetado para uso com Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e` , que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="60ae6-108">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="60ae6-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="60ae6-109">Robust Programming</span></span>  
 <span data-ttu-id="60ae6-110">Você sempre deve chamar <xref:System.IDisposable.Dispose%2A> todos os objetos que consomem recursos do sistema, como <xref:System.Drawing.Pen> objetos.</span><span class="sxs-lookup"><span data-stu-id="60ae6-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ae6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60ae6-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawLine%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="60ae6-112">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="60ae6-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="60ae6-113">Uso de uma caneta para desenhar linhas e formas</span><span class="sxs-lookup"><span data-stu-id="60ae6-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="60ae6-114">Elementos gráficos e desenho no Windows Forms</span><span class="sxs-lookup"><span data-stu-id="60ae6-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
