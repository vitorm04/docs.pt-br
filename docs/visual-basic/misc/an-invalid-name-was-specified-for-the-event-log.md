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
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="992e7-102">Um nome inválido foi especificado para o log de eventos</span><span class="sxs-lookup"><span data-stu-id="992e7-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="992e7-103">Um nome inválido foi especificado para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="992e7-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="992e7-104">Geralmente, isso é um resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.</span><span class="sxs-lookup"><span data-stu-id="992e7-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="992e7-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="992e7-105">To correct this error</span></span>  
  
-   <span data-ttu-id="992e7-106">Se o nome especificado é de mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="992e7-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="992e7-107">Apenas os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="992e7-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="992e7-108">Se fornecer um caminho, verifique se que ele é analisado corretamente.</span><span class="sxs-lookup"><span data-stu-id="992e7-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="992e7-109">Verificar não se há nenhum caractere inválido no nome.</span><span class="sxs-lookup"><span data-stu-id="992e7-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="992e7-110">Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.</span><span class="sxs-lookup"><span data-stu-id="992e7-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="992e7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="992e7-111">See Also</span></span>  
 [<span data-ttu-id="992e7-112">Como analisar demarcadores de arquivo</span><span class="sxs-lookup"><span data-stu-id="992e7-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [<span data-ttu-id="992e7-113">Como renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="992e7-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="992e7-114">Como: criar e remover os Logs de eventos personalizados</span><span class="sxs-lookup"><span data-stu-id="992e7-114">How to: Create and Remove Custom Event Logs</span></span>](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
