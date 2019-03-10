---
title: 'Como: Carregar e exibir metarquivos'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 121f285a95d0169db79bdc302d80dba03b3b40c2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720037"
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="0903b-102">Como: Carregar e exibir metarquivos</span><span class="sxs-lookup"><span data-stu-id="0903b-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="0903b-103">O <xref:System.Drawing.Imaging.Metafile> classe, que herda o <xref:System.Drawing.Image> de classe, que fornece métodos para gravar, exibir e examinar imagens vetoriais.</span><span class="sxs-lookup"><span data-stu-id="0903b-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0903b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0903b-104">Example</span></span>  
 <span data-ttu-id="0903b-105">Para exibir uma imagem de vetor (metarquivo) na tela, você precisa de uma <xref:System.Drawing.Imaging.Metafile> objeto e um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="0903b-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0903b-106">Passe o nome de um arquivo (ou um fluxo) para um <xref:System.Drawing.Imaging.Metafile> construtor.</span><span class="sxs-lookup"><span data-stu-id="0903b-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="0903b-107">Depois de criar uma <xref:System.Drawing.Imaging.Metafile> de objeto, passá-lo <xref:System.Drawing.Imaging.Metafile> do objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="0903b-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="0903b-108">O exemplo cria um <xref:System.Drawing.Imaging.Metafile> objeto a partir de um arquivo EMF (metarquivo avançado) e, em seguida, desenha a imagem com seu canto superior esquerdo em (60, 10).</span><span class="sxs-lookup"><span data-stu-id="0903b-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="0903b-109">A ilustração a seguir mostra o metarquivo desenhado no local especificado.</span><span class="sxs-lookup"><span data-stu-id="0903b-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="0903b-110">![Posição da imagem](./media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="0903b-110">![Image Position](./media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0903b-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="0903b-111">Compiling the Code</span></span>  
 <span data-ttu-id="0903b-112">O exemplo anterior foi projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="0903b-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0903b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0903b-113">See also</span></span>
- [<span data-ttu-id="0903b-114">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="0903b-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
