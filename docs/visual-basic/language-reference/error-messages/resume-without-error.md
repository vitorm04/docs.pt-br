---
title: Retomar sem erro
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="a19b6-102">Retomar sem erro</span><span class="sxs-lookup"><span data-stu-id="a19b6-102">Resume without error</span></span>
<span data-ttu-id="a19b6-103">Um `Resume` instrução apareceu fora do código de tratamento de erros ou o código pular para um manipulador de erro, embora nenhum erro.</span><span class="sxs-lookup"><span data-stu-id="a19b6-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a19b6-104">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="a19b6-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a19b6-105">Mover o `Resume` instrução em um manipulador de erro, ou excluí-lo.</span><span class="sxs-lookup"><span data-stu-id="a19b6-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="a19b6-106">Portanto saltos para rótulos não podem ocorrer em vários procedimentos, pesquise o procedimento para o rótulo que identifica o manipulador de erro.</span><span class="sxs-lookup"><span data-stu-id="a19b6-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="a19b6-107">Se você encontrar um rótulo duplicado especificado como o destino de uma `GoTo` instrução que não é um `On Error GoTo` instrução, alterar o rótulo de linha de acordo com seu destino pretendido.</span><span class="sxs-lookup"><span data-stu-id="a19b6-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a19b6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a19b6-108">See Also</span></span>  
 [<span data-ttu-id="a19b6-109">Instrução Resume</span><span class="sxs-lookup"><span data-stu-id="a19b6-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="a19b6-110">Instrução On Error</span><span class="sxs-lookup"><span data-stu-id="a19b6-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
