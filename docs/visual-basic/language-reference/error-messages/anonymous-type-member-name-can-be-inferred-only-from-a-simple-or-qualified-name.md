---
title: O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7068928a17ee5fdb7bf6b5e0a40aaa7e5ef32f11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
Não é possível inferir um nome de membro de tipo anônimo de uma expressão complexa.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Para obter mais informações sobre as fontes do qual os tipos anônimos podem e não é possível inferir os tipos e nomes de membros, consulte [como: inferir nomes de propriedade e tipos de declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **ID do erro:** BC36556  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribua a expressão a um nome de membro, conforme mostrado no código a seguir:  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos Anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
