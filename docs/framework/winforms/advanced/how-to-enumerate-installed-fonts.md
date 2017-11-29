---
title: Como enumerar as fontes instaladas
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
- fonts [Windows Forms], enumerating installed
- examples [Windows Forms], fonts
ms.assetid: 26d74ef5-0f39-4eeb-8d20-00e66e014abe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bca536ed2f3e493e8d50fe8f1a0115327f1d8720
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-enumerate-installed-fonts"></a><span data-ttu-id="a30c1-102">Como enumerar as fontes instaladas</span><span class="sxs-lookup"><span data-stu-id="a30c1-102">How to: Enumerate Installed Fonts</span></span>
<span data-ttu-id="a30c1-103">O <xref:System.Drawing.Text.InstalledFontCollection> classe herda o <xref:System.Drawing.Text.FontCollection> classe base abstrata.</span><span class="sxs-lookup"><span data-stu-id="a30c1-103">The <xref:System.Drawing.Text.InstalledFontCollection> class inherits from the <xref:System.Drawing.Text.FontCollection> abstract base class.</span></span> <span data-ttu-id="a30c1-104">Você pode usar um <xref:System.Drawing.Text.InstalledFontCollection> objeto para enumerar as fontes instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="a30c1-104">You can use an <xref:System.Drawing.Text.InstalledFontCollection> object to enumerate the fonts installed on the computer.</span></span> <span data-ttu-id="a30c1-105">O <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade de um <xref:System.Drawing.Text.InstalledFontCollection> objeto é uma matriz de <xref:System.Drawing.FontFamily> objetos.</span><span class="sxs-lookup"><span data-stu-id="a30c1-105">The <xref:System.Drawing.Text.FontCollection.Families%2A> property of an <xref:System.Drawing.Text.InstalledFontCollection> object is an array of <xref:System.Drawing.FontFamily> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a30c1-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a30c1-106">Example</span></span>  
 <span data-ttu-id="a30c1-107">O exemplo a seguir lista os nomes de todas as famílias de fontes instaladas no computador.</span><span class="sxs-lookup"><span data-stu-id="a30c1-107">The following example lists the names of all the font families installed on the computer.</span></span> <span data-ttu-id="a30c1-108">O código recupera o <xref:System.Drawing.FontFamily.Name%2A> propriedade de cada <xref:System.Drawing.FontFamily> objeto na matriz retornada pelo <xref:System.Drawing.Text.FontCollection.Families%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="a30c1-108">The code retrieves the <xref:System.Drawing.FontFamily.Name%2A> property of each <xref:System.Drawing.FontFamily> object in the array returned by the <xref:System.Drawing.Text.FontCollection.Families%2A> property.</span></span> <span data-ttu-id="a30c1-109">Como os nomes de família são recuperados, eles são concatenados à lista de formulário um separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="a30c1-109">As the family names are retrieved, they are concatenated to form a comma-separated list.</span></span> <span data-ttu-id="a30c1-110">Em seguida, o <xref:System.Drawing.Graphics.DrawString%2A> método o <xref:System.Drawing.Graphics> classe desenha a lista separada por vírgulas em um retângulo.</span><span class="sxs-lookup"><span data-stu-id="a30c1-110">Then the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class draws the comma-separated list in a rectangle.</span></span>  
  
 <span data-ttu-id="a30c1-111">Se você executar o código de exemplo, a saída será semelhante ao mostrado na ilustração a seguir.</span><span class="sxs-lookup"><span data-stu-id="a30c1-111">If you run the example code, the output will be similar to that shown in the following illustration.</span></span>  
  
 <span data-ttu-id="a30c1-112">![Fontes instaladas](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span><span class="sxs-lookup"><span data-stu-id="a30c1-112">![Installed Fonts](../../../../docs/framework/winforms/advanced/media/csfontstext6.png "csfontstext6")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.FontsAndText#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a30c1-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a30c1-113">Compiling the Code</span></span>  
 <span data-ttu-id="a30c1-114">O exemplo anterior é projetado para uso com o Windows Forms e requer <xref:System.Windows.Forms.PaintEventArgs> `e`, que é um parâmetro de <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a30c1-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span> <span data-ttu-id="a30c1-115">Além disso, você deve importar o <xref:System.Drawing.Text> namespace.</span><span class="sxs-lookup"><span data-stu-id="a30c1-115">In addition, you should import the <xref:System.Drawing.Text> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a30c1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a30c1-116">See Also</span></span>  
 [<span data-ttu-id="a30c1-117">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="a30c1-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
