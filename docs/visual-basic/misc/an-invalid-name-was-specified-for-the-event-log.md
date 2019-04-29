---
title: Um nome inválido foi especificado para o log de eventos
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 2b9c934272d0f3392c845dcd2f0062a98dc50c7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940667"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="3f579-102">Um nome inválido foi especificado para o log de eventos</span><span class="sxs-lookup"><span data-stu-id="3f579-102">An invalid name was specified for the event log</span></span>
<span data-ttu-id="3f579-103">Um nome inválido foi especificado para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="3f579-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="3f579-104">Normalmente, este é um resultado de caracteres inválidos no nome da, um nome de arquivo em branco ou um nome de arquivo é muito longo.</span><span class="sxs-lookup"><span data-stu-id="3f579-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f579-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="3f579-105">To correct this error</span></span>  
  
- <span data-ttu-id="3f579-106">Se o nome especificado é a mais de oito caracteres, verifique se que há nenhum conflito com os nomes dos outros logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="3f579-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="3f579-107">Somente os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3f579-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="3f579-108">Se você estiver fornecendo um caminho, certifique-se de que ele é analisado corretamente.</span><span class="sxs-lookup"><span data-stu-id="3f579-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="3f579-109">Verifique não se há nenhum caractere inválido no nome.</span><span class="sxs-lookup"><span data-stu-id="3f579-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="3f579-110">Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.</span><span class="sxs-lookup"><span data-stu-id="3f579-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f579-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f579-111">See also</span></span>

- [<span data-ttu-id="3f579-112">Como: Analisar caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="3f579-112">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="3f579-113">Como: Renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="3f579-113">How to: Rename a File</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
