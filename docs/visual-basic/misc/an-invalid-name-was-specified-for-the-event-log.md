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
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Um nome inválido foi especificado para o log de evento

Um nome inválido foi especificado para o log de eventos. Normalmente, isso é resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo muito longo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se o nome especificado tiver mais de oito caracteres, verifique se não há conflito com os nomes de outros logs de eventos. Somente os oito primeiros caracteres são avaliados ao determinar se o nome é exclusivo.  
  
- Se fornecer um caminho, verifique se ele foi analisado corretamente.  
  
- Verifique se não há caracteres inválidos no nome. Os caracteres que não podem ser usados em um nome de arquivo incluem `<` , `>` ,,,, `:` `"` `/` `\` e `|` .  
  
## <a name="see-also"></a>Confira também

- [Como: analisar caminhos de arquivo](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
- [Como: renomear um arquivo](../developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
