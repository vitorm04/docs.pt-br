---
title: "Número de registro incorreto | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
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
ms.openlocfilehash: 640484e24af55abc76d3e2e1a4680624ae98974e
ms.lasthandoff: 03/13/2017

---
# <a name="bad-record-number"></a>Número de registro incorreto
O número do registro em `a FileGet`, `FilePut`, `FileGetObject`, ou `FilePutObject` instrução é menor ou igual a zero.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique os cálculos usados na geração de número de registro. Verifique se as variáveis contendo o número de registro ou usado para calcular números de registro. Um nome de variável digitado incorretamente é implicitamente declarado e inicializado como zero, a menos que você usou `Option Explicit On` no módulo.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Option Explicit](../../visual-basic/language-reference/statements/option-explicit-statement.md)
