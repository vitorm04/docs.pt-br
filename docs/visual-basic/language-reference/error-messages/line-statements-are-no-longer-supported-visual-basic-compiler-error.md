---
title: '&#39;Linha&#39; instruções não são mais compatíveis (erro do compilador Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 36226cc371ffb8a51cb8d0f918952f1c717aea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702959"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="f71dd-102">&#39;Linha&#39; instruções não são mais compatíveis (erro do compilador Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f71dd-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="f71dd-103">Não há suporte para instruções de linha.</span><span class="sxs-lookup"><span data-stu-id="f71dd-103">Line statements are no longer supported.</span></span> <span data-ttu-id="f71dd-104">Funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e a funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="f71dd-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="f71dd-105">**ID do erro:** BC30830</span><span class="sxs-lookup"><span data-stu-id="f71dd-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f71dd-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f71dd-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f71dd-107">Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="f71dd-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="f71dd-108">Se executar gráficos, use `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="f71dd-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f71dd-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f71dd-109">See also</span></span>
- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="f71dd-110">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f71dd-110">File Access with Visual Basic</span></span>](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
