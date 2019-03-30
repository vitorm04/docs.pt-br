---
title: 'Como: Desenhar um Bitmap existente na tela'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: d2e06aa382bc2b01a4308f99735ca533e7a9a3ea
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653815"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a><span data-ttu-id="87b6c-102">Como: Desenhar um Bitmap existente na tela</span><span class="sxs-lookup"><span data-stu-id="87b6c-102">How to: Draw an Existing Bitmap to the Screen</span></span>
<span data-ttu-id="87b6c-103">É possível desenhar facilmente uma imagem existente na tela.</span><span class="sxs-lookup"><span data-stu-id="87b6c-103">You can easily draw an existing image on the screen.</span></span> <span data-ttu-id="87b6c-104">Primeiro você precisa criar uma <xref:System.Drawing.Bitmap> objeto usando o construtor de bitmap que usa um nome de arquivo <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="87b6c-104">First you need to create a <xref:System.Drawing.Bitmap> object by using the bitmap constructor that takes a file name, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>.</span></span> <span data-ttu-id="87b6c-105">Este construtor aceita imagens com vários formatos de arquivo diferentes, incluindo BMP, GIF, JPEG, PNG e TIFF.</span><span class="sxs-lookup"><span data-stu-id="87b6c-105">This constructor accepts images with several different file formats, including BMP, GIF, JPEG, PNG, and TIFF.</span></span> <span data-ttu-id="87b6c-106">Depois que você criou o <xref:System.Drawing.Bitmap> de objeto, passá-lo <xref:System.Drawing.Bitmap> do objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="87b6c-106">After you have created the <xref:System.Drawing.Bitmap> object, pass that <xref:System.Drawing.Bitmap> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b6c-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87b6c-107">Example</span></span>  
 <span data-ttu-id="87b6c-108">Este exemplo cria um <xref:System.Drawing.Bitmap> objeto de um arquivo JPEG e, em seguida, desenha o bitmap com seu canto superior esquerdo em (60, 10).</span><span class="sxs-lookup"><span data-stu-id="87b6c-108">This example creates a <xref:System.Drawing.Bitmap> object from a JPEG file and then draws the bitmap with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="87b6c-109">A ilustração a seguir mostra o bitmap desenhado no local especificado:</span><span class="sxs-lookup"><span data-stu-id="87b6c-109">The following illustration shows the bitmap drawn at the specified location:</span></span>  
  
 ![Captura de tela que mostra uma imagem em uma posição especificada.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="87b6c-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="87b6c-111">Compiling the Code</span></span>  
 <span data-ttu-id="87b6c-112">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="87b6c-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b6c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87b6c-113">See also</span></span>
- [<span data-ttu-id="87b6c-114">Elementos Gráficos e Desenho nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87b6c-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="87b6c-115">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="87b6c-115">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
