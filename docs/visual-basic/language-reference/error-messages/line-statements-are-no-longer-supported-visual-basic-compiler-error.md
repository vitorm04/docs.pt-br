---
title: "Instruções &quot;Line&quot; não são mais compatíveis (erro do compilador Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
dev_langs:
- VB
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 92993a2a3d9ee34ab0071034b9e8ebe3b1180b0a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a><span data-ttu-id="f4998-102">Instruções 'Line' não são mais compatíveis (erro do compilador Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4998-102">&#39;Line&#39; statements are no longer supported (Visual Basic Compiler Error)</span></span>
<span data-ttu-id="f4998-103">Não há suporte para instruções de linha.</span><span class="sxs-lookup"><span data-stu-id="f4998-103">Line statements are no longer supported.</span></span> <span data-ttu-id="f4998-104">A funcionalidade de e/s de arquivo está disponível como `Microsoft.VisualBasic.FileSystem.LineInput` e funcionalidade de elementos gráficos está disponível como `System.Drawing.Graphics.DrawLine`.</span><span class="sxs-lookup"><span data-stu-id="f4998-104">File I/O functionality is available as `Microsoft.VisualBasic.FileSystem.LineInput` and graphics functionality is available as `System.Drawing.Graphics.DrawLine`.</span></span>  
  
 <span data-ttu-id="f4998-105">**ID do erro:** BC30830</span><span class="sxs-lookup"><span data-stu-id="f4998-105">**Error ID:** BC30830</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4998-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="f4998-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="f4998-107">Se executar o acesso a arquivos, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span><span class="sxs-lookup"><span data-stu-id="f4998-107">If performing file access, use `Microsoft.VisualBasic.FileSystem.LineInput`.</span></span>  
  
2.  <span data-ttu-id="f4998-108">Se executar gráficos, use `System.Drawing.Graphics.Drawline`.</span><span class="sxs-lookup"><span data-stu-id="f4998-108">If performing graphics, use `System.Drawing.Graphics.Drawline`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4998-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4998-109">See Also</span></span>  
 <span data-ttu-id="f4998-110"><xref:System.IO></xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="f4998-110"><xref:System.IO></span></span>   
 <span data-ttu-id="f4998-111"><xref:System.Drawing></xref:System.Drawing></span><span class="sxs-lookup"><span data-stu-id="f4998-111"><xref:System.Drawing></span></span>   
<span data-ttu-id="f4998-112"> [Access de arquivo com o Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)</span><span class="sxs-lookup"><span data-stu-id="f4998-112"> [File Access with Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)</span></span>
