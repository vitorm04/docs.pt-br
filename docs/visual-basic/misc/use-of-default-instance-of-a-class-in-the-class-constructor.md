---
title: "Uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: c4b9db1576e7a96c4d8d7236edd8324e8d846fe4
ms.lasthandoff: 03/13/2017

---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a>Uso de instância padrão de uma classe no construtor de classe pode levar a chamada recursiva infinita
Uma instância padrão de uma classe foi usada no construtor da classe. Isso pode levar a uma chamada recursiva infinita, também conhecido como um loop infinito.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Remova a instância padrão do construtor da classe.  
  
## <a name="see-also"></a>Consulte também  
 [NÃO está em compilação: Usando construtores e destruidores](http://msdn.microsoft.com/en-us/548eebe1-86c4-4377-b2f5-447cb8be3d90)
