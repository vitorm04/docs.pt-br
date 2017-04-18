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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d41d2038aba9c2549a3d1fac1b982df7399280f3
ms.lasthandoff: 03/13/2017

---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Um nome inválido foi especificado para o log de eventos
Um nome inválido foi especificado para o log de eventos. Geralmente, isso é resultado dos caracteres inválidos no nome, um nome de arquivo em branco ou um nome de arquivo é muito longo.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se o nome especificado é mais de oito caracteres, verifique se que não há nenhum conflito com os nomes dos outros logs de eventos. Somente os oito primeiros caracteres são avaliados para determinar se o nome é exclusivo.  
  
-   Se fornecer um caminho, verifique se que ele é analisado corretamente.  
  
-   Verificar não se há nenhum caractere inválido no nome. Incluem caracteres que não podem ser usados em um nome de arquivo `<`, `>`, `:`, `"`, `/`, `\`, e `|`.  
  
## <a name="see-also"></a>Consulte também  
 [Como: analisar caminhos de arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)   
 [Como: renomear um arquivo](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [Como: criar e remover os Logs de eventos personalizados](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
