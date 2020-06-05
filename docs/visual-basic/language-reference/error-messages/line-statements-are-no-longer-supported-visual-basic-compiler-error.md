---
title: Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397292"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="05063-102">Instruções 'Line' não são mais compatíveis (erro de compilador do Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05063-102">'Line' statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="05063-103">Não há mais suporte para instruções de linha.</span><span class="sxs-lookup"><span data-stu-id="05063-103">Line statements are no longer supported.</span></span> <span data-ttu-id="05063-104">A funcionalidade de e/s de arquivo está disponível `Microsoft.VisualBasic.FileSystem.LineInput` e a funcionalidade de gráficos está disponível como `System.Drawing.Graphics.DrawLine` .</span><span class="sxs-lookup"><span data-stu-id="05063-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="05063-105">**ID do erro:** BC30830</span><span class="sxs-lookup"><span data-stu-id="05063-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="05063-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="05063-106">To correct this error</span></span>  
  
1. <span data-ttu-id="05063-107">Se estiver executando o acesso ao arquivo, use `Microsoft.VisualBasic.FileSystem.LineInput` .</span><span class="sxs-lookup"><span data-stu-id="05063-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2. <span data-ttu-id="05063-108">Se estiver executando gráficos, use `System.Drawing.Graphics.Drawline` .</span><span class="sxs-lookup"><span data-stu-id="05063-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05063-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="05063-109">See also</span></span>

- <xref:System.IO>
- <xref:System.Drawing>
- [<span data-ttu-id="05063-110">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05063-110">File Access with Visual Basic</span></span>](../../developing-apps/programming/drives-directories-files/file-access.md)
