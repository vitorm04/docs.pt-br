---
title: "Um nome inválido foi especificado para o log de eventos"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="701e1-102">Um nome inválido foi especificado para o log de eventos</span><span class="sxs-lookup"><span data-stu-id="701e1-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="701e1-103">Um nome inválido foi especificado para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="701e1-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="701e1-104">Geralmente, isso é um resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.</span><span class="sxs-lookup"><span data-stu-id="701e1-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="701e1-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="701e1-105">To correct this error</span></span>  
  
-   <span data-ttu-id="701e1-106">Se o nome especificado é de mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="701e1-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="701e1-107">Apenas os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="701e1-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="701e1-108">Se fornecer um caminho, verifique se que ele é analisado corretamente.</span><span class="sxs-lookup"><span data-stu-id="701e1-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="701e1-109">Verificar não se há nenhum caractere inválido no nome.</span><span class="sxs-lookup"><span data-stu-id="701e1-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="701e1-110">Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.</span><span class="sxs-lookup"><span data-stu-id="701e1-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701e1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="701e1-111">See Also</span></span>  
 [<span data-ttu-id="701e1-112">Como analisar demarcadores de arquivo</span><span class="sxs-lookup"><span data-stu-id="701e1-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="701e1-113">Como renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="701e1-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
