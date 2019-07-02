---
title: Metarquivos no GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504595"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="2ed3e-102">Metarquivos no GDI+</span><span class="sxs-lookup"><span data-stu-id="2ed3e-102">Metafiles in GDI+</span></span>
<span data-ttu-id="2ed3e-103">GDI+ fornece o <xref:System.Drawing.Imaging.Metafile> de classe para que você pode registrar e exibir metarquivos.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="2ed3e-104">Um metarquivo, também chamado de uma imagem de vetor, é uma imagem que é armazenada como uma sequência de comandos e configurações de desenho.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="2ed3e-105">Os comandos e configurações registrados em um <xref:System.Drawing.Imaging.Metafile> objeto pode ser armazenado na memória ou salvos em um arquivo ou fluxo.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="2ed3e-106">Formatos de metarquivos</span><span class="sxs-lookup"><span data-stu-id="2ed3e-106">Metafile Formats</span></span>  
 <span data-ttu-id="2ed3e-107">GDI+ pode exibir metarquivos que foram armazenados nos seguintes formatos:</span><span class="sxs-lookup"><span data-stu-id="2ed3e-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="2ed3e-108">Metarquivo do Windows (WMF)</span><span class="sxs-lookup"><span data-stu-id="2ed3e-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="2ed3e-109">EMF (Metarquivo Avançado)</span><span class="sxs-lookup"><span data-stu-id="2ed3e-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="2ed3e-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="2ed3e-110">EMF+</span></span>  
  
 <span data-ttu-id="2ed3e-111">GDI+ pode registrar metarquivos nos formatos EMF e EMF +, mas não no formato WMF.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="2ed3e-112">EMF + é uma extensão de EMF que permite que os registros de GDI+ a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="2ed3e-113">Há duas variações no formato EMF +: EMF + somente e EMF + duplo.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="2ed3e-114">Metarquivos apenas EMF + contêm apenas registros de GDI+.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="2ed3e-115">Esses metarquivos podem ser exibidos por GDI+, mas não por GDI.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="2ed3e-116">Metarquivos EMF + duplos contêm registros GDI+ e GDI.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="2ed3e-117">Cada registro de GDI+ em um metarquivo EMF + duplo é emparelhado com um registro GDI alternativo.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="2ed3e-118">Esses metarquivos podem ser exibidos por GDI+ ou por GDI.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="2ed3e-119">O exemplo a seguir exibe um metarquivo que foi salvo anteriormente como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2ed3e-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="2ed3e-120">O metarquivo é exibido com seu canto superior esquerdo em (100, 100).</span><span class="sxs-lookup"><span data-stu-id="2ed3e-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="2ed3e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ed3e-121">See also</span></span>

- [<span data-ttu-id="2ed3e-122">Imagens, bitmaps e metarquivos</span><span class="sxs-lookup"><span data-stu-id="2ed3e-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
