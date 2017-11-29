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
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Um nome inválido foi especificado para o log de eventos
Um nome inválido foi especificado para o log de eventos. Geralmente, isso é um resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o nome especificado é de mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos. Apenas os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.  
  
-   Se fornecer um caminho, verifique se que ele é analisado corretamente.  
  
-   Verificar não se há nenhum caractere inválido no nome. Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.  
  
## <a name="see-also"></a>Consulte também  
 [Como analisar demarcadores de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [Como renomear um arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Como: criar e remover os Logs de eventos personalizados](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
