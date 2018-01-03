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
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Um nome inválido foi especificado para o log de eventos
Um nome inválido foi especificado para o log de eventos. Geralmente, isso é um resultado de caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o nome especificado é de mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos. Apenas os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.  
  
-   Se fornecer um caminho, verifique se que ele é analisado corretamente.  
  
-   Verificar não se há nenhum caractere inválido no nome. Caracteres que não podem ser usados em um nome de arquivo incluem `<`, `>`, `:`, `"`, `/`, `\`, e `|`.  
  
## <a name="see-also"></a>Consulte também  
 [Como analisar demarcadores de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [Como renomear um arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 
