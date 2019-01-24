---
title: Um nome inválido foi especificado para o log de eventos
ms.date: 07/20/2015
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
ms.openlocfilehash: 242c5394011fd018a03f81b9b56bcfd7015682dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604386"
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Um nome inválido foi especificado para o log de eventos
Um nome inválido foi especificado para o log de eventos. Normalmente, este é um resultado de caracteres inválidos no nome da, um nome de arquivo em branco ou um nome de arquivo é muito longo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o nome especificado é a mais de oito caracteres, verifique se que há nenhum conflito com os nomes dos outros logs de eventos. Somente os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.  
  
-   Se você estiver fornecendo um caminho, certifique-se de que ele é analisado corretamente.  
  
-   Verifique não se há nenhum caractere inválido no nome. Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.  
  
## <a name="see-also"></a>Consulte também
- [Como: Analisar demarcadores de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Como: Renomear um arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

