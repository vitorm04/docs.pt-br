---
title: Retomar sem erro | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
dev_langs:
- VB
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
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
ms.openlocfilehash: a86bbebf634acf1c0f1395d1e5f490161d09452e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="resume-without-error"></a><span data-ttu-id="08e94-102">Retomar sem erro</span><span class="sxs-lookup"><span data-stu-id="08e94-102">Resume without error</span></span>
<span data-ttu-id="08e94-103">Um `Resume` instrução apareceu fora do código de tratamento de erros, ou o código entrou em um manipulador de erro mesmo que não houve erro.</span><span class="sxs-lookup"><span data-stu-id="08e94-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08e94-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="08e94-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="08e94-105">Mova o `Resume`instrução em um manipulador de erro, ou excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="08e94-105">Move the `Resume`statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="08e94-106">Então vai para rótulos não pode ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="08e94-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="08e94-107">Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é um `On Error GoTo` instrução, alterar o rótulo de linha de acordo com seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="08e94-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08e94-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08e94-108">See Also</span></span>  
 <span data-ttu-id="08e94-109">[Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md) </span><span class="sxs-lookup"><span data-stu-id="08e94-109">[Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md) </span></span>  
<span data-ttu-id="08e94-110"> [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)</span><span class="sxs-lookup"><span data-stu-id="08e94-110"> [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)</span></span>
