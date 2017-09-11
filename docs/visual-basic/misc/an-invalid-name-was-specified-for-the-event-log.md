---
title: "Um nome inválido foi especificado para o log de eventos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 53e9c563c44cb44f82f0a9054383b10311616831
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="d7865-102">Um nome inválido foi especificado para o log de eventos</span><span class="sxs-lookup"><span data-stu-id="d7865-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="d7865-103">Um nome inválido foi especificado para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="d7865-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="d7865-104">Geralmente, isso é resultado dos caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.</span><span class="sxs-lookup"><span data-stu-id="d7865-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d7865-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d7865-105">To correct this error</span></span>  
  
-   <span data-ttu-id="d7865-106">Se o nome especificado é mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="d7865-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="d7865-107">Somente os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="d7865-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
-   <span data-ttu-id="d7865-108">Se fornecer um caminho, verifique se que ele é analisado corretamente.</span><span class="sxs-lookup"><span data-stu-id="d7865-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
-   <span data-ttu-id="d7865-109">Verificar não se há nenhum caractere inválido no nome.</span><span class="sxs-lookup"><span data-stu-id="d7865-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="d7865-110">Incluem caracteres que não podem ser usados em um nome de arquivo `<`, `>`, `:`, `"`, `/`, `\`, e `|`.</span><span class="sxs-lookup"><span data-stu-id="d7865-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7865-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7865-111">See Also</span></span>  
 <span data-ttu-id="d7865-112">[Como: analisar caminhos de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md) </span><span class="sxs-lookup"><span data-stu-id="d7865-112">[How to: Parse File Paths](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md) </span></span>  
<span data-ttu-id="d7865-113"> [Como: renomear um arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="d7865-113"> [How to: Rename a File](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span></span>  
<span data-ttu-id="d7865-114"> [Como: criar e remover os Logs de eventos personalizados](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)</span><span class="sxs-lookup"><span data-stu-id="d7865-114"> [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)</span></span>
