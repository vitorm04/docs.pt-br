---
title: Um nome inválido foi especificado para o log de evento
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 36e2bc91a671a22e808d0e30e292471729b1e50b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083872"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a><span data-ttu-id="85ff4-102">Um nome inválido foi especificado para o log de evento</span><span class="sxs-lookup"><span data-stu-id="85ff4-102">An invalid name was specified for the event log</span></span>

<span data-ttu-id="85ff4-103">Um nome inválido foi especificado para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="85ff4-103">An invalid name was specified for the event log.</span></span> <span data-ttu-id="85ff4-104">Normalmente, isso é resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo muito longo.</span><span class="sxs-lookup"><span data-stu-id="85ff4-104">Usually this is a result of invalid characters in the name, a blank file name, or a file name that is too long.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="85ff4-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="85ff4-105">To correct this error</span></span>  
  
- <span data-ttu-id="85ff4-106">Se o nome especificado tiver mais de oito caracteres, verifique se não há conflito com os nomes de outros logs de eventos.</span><span class="sxs-lookup"><span data-stu-id="85ff4-106">If the specified name is more than eight characters, make sure there is no conflict with the names of other event logs.</span></span> <span data-ttu-id="85ff4-107">Somente os oito primeiros caracteres são avaliados ao determinar se o nome é exclusivo.</span><span class="sxs-lookup"><span data-stu-id="85ff4-107">Only the first eight characters are evaluated when determining if the name is unique.</span></span>  
  
- <span data-ttu-id="85ff4-108">Se fornecer um caminho, verifique se ele foi analisado corretamente.</span><span class="sxs-lookup"><span data-stu-id="85ff4-108">If supplying a path, make sure it is parsed correctly.</span></span>  
  
- <span data-ttu-id="85ff4-109">Verifique se não há caracteres inválidos no nome.</span><span class="sxs-lookup"><span data-stu-id="85ff4-109">Check that there are no invalid characters in the name.</span></span> <span data-ttu-id="85ff4-110">Os caracteres que não podem ser usados em um nome de arquivo incluem `<` , `>` ,,,, `:` `"` `/` `\` e `|` .</span><span class="sxs-lookup"><span data-stu-id="85ff4-110">Characters that cannot be used in a file name include `<`, `>`, `:`, `"`, `/`, `\`, and `|`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ff4-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="85ff4-111">See also</span></span>

- [<span data-ttu-id="85ff4-112">Como: analisar caminhos de arquivo</span><span class="sxs-lookup"><span data-stu-id="85ff4-112">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [<span data-ttu-id="85ff4-113">Como: renomear um arquivo</span><span class="sxs-lookup"><span data-stu-id="85ff4-113">How to: Rename a File</span></span>](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
