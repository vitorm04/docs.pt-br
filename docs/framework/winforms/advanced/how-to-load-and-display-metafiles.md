---
title: Como carregar e exibir metarquivos
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722b6d36801c69e500535a32e952ef8f45634d03
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-load-and-display-metafiles"></a><span data-ttu-id="01eaf-102">Como carregar e exibir metarquivos</span><span class="sxs-lookup"><span data-stu-id="01eaf-102">How to: Load and Display Metafiles</span></span>
<span data-ttu-id="01eaf-103">O <xref:System.Drawing.Imaging.Metafile> classe que herde o <xref:System.Drawing.Image> da classe, fornece métodos para registrar, exibir e examinar as imagens de vetor.</span><span class="sxs-lookup"><span data-stu-id="01eaf-103">The <xref:System.Drawing.Imaging.Metafile> class, which inherits from the <xref:System.Drawing.Image> class, provides methods for recording, displaying, and examining vector images.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01eaf-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="01eaf-104">Example</span></span>  
 <span data-ttu-id="01eaf-105">Para exibir uma imagem de vetor (metarquivo) na tela, é necessário um <xref:System.Drawing.Imaging.Metafile> objeto e um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="01eaf-105">To display a vector image (metafile) on the screen, you need a <xref:System.Drawing.Imaging.Metafile> object and a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="01eaf-106">Passe o nome de um arquivo (ou um fluxo) para um <xref:System.Drawing.Imaging.Metafile> construtor.</span><span class="sxs-lookup"><span data-stu-id="01eaf-106">Pass the name of a file (or a stream) to a <xref:System.Drawing.Imaging.Metafile> constructor.</span></span> <span data-ttu-id="01eaf-107">Depois de ter criado um <xref:System.Drawing.Imaging.Metafile> de objeto, passe que <xref:System.Drawing.Imaging.Metafile> o objeto para o <xref:System.Drawing.Graphics.DrawImage%2A> método de um <xref:System.Drawing.Graphics> objeto.</span><span class="sxs-lookup"><span data-stu-id="01eaf-107">After you have created a <xref:System.Drawing.Imaging.Metafile> object, pass that <xref:System.Drawing.Imaging.Metafile> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 <span data-ttu-id="01eaf-108">O exemplo cria um <xref:System.Drawing.Imaging.Metafile> objeto a partir de um arquivo EMF (metarquivo avançado) e, em seguida, desenha a imagem com seu canto superior esquerdo no (60, 10).</span><span class="sxs-lookup"><span data-stu-id="01eaf-108">The example creates a <xref:System.Drawing.Imaging.Metafile> object from an EMF (enhanced metafile) file and then draws the image with its upper-left corner at (60, 10).</span></span>  
  
 <span data-ttu-id="01eaf-109">A ilustração a seguir mostra o metarquivo desenhado no local especificado.</span><span class="sxs-lookup"><span data-stu-id="01eaf-109">The following illustration shows the metafile drawn at the specified location.</span></span>  
  
 <span data-ttu-id="01eaf-110">![Posição da imagem](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span><span class="sxs-lookup"><span data-stu-id="01eaf-110">![Image Position](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="01eaf-111">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="01eaf-111">Compiling the Code</span></span>  
 <span data-ttu-id="01eaf-112">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro do <xref:System.Windows.Forms.Control.Paint> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="01eaf-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01eaf-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01eaf-113">See Also</span></span>  
 [<span data-ttu-id="01eaf-114">Trabalhando com Imagens, Bitmaps, Ícones e Metarquivos</span><span class="sxs-lookup"><span data-stu-id="01eaf-114">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
