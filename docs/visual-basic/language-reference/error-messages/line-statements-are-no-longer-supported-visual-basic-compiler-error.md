---
title: Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 17025e9a3c87d84a10ddaa7aeef616d985143879
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283192"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="2baad-102">Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2baad-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="2baad-103">Não há suporte para instruções de linha.</span><span class="sxs-lookup"><span data-stu-id="2baad-103">Line statements are no longer supported.</span></span> <span data-ttu-id="2baad-104">Funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e a funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="2baad-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="2baad-105">**ID do erro:** BC30830</span><span class="sxs-lookup"><span data-stu-id="2baad-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2baad-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="2baad-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2baad-107">Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="2baad-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="2baad-108">Se executar gráficos, use `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="2baad-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2baad-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2baad-109">See also</span></span>
- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="2baad-110">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2baad-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
