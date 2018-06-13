---
title: '&#39;Linha&#39; instruções não são mais suportados (erro de compilador do Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587873"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="7f421-102">&#39;Linha&#39; instruções não são mais suportados (erro de compilador do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f421-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="7f421-103">Não há suporte para instruções de linha.</span><span class="sxs-lookup"><span data-stu-id="7f421-103">Line statements are no longer supported.</span></span> <span data-ttu-id="7f421-104">A funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="7f421-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="7f421-105">**ID do erro:** BC30830</span><span class="sxs-lookup"><span data-stu-id="7f421-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7f421-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7f421-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7f421-107">Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="7f421-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="7f421-108">Se estiver executando o gráfico, use `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="7f421-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f421-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f421-109">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [<span data-ttu-id="7f421-110">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7f421-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
