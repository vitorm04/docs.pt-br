---
title: "Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
dev_langs:
- VB
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e797e247abb3323c4e1280cd500b5ef006f700e
ms.lasthandoff: 03/13/2017

---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Parâmetros genéricos usados como tipos de parâmetro opcionais devem ter a classe restrita
Um procedimento é declarado com um parâmetro opcional que usa um parâmetro de tipo que não está restrito a ser um tipo de referência.  
  
 Você sempre deve fornecer um valor padrão para cada parâmetro opcional. Se o parâmetro é de um tipo de referência, o valor opcional deve ser `Nothing`, que é um valor válido para qualquer tipo de referência. No entanto, se o parâmetro é de um tipo de valor, esse tipo deve ser um tipo de dados elementar predefinido pelo Visual Basic. Isso ocorre porque um tipo de valor composto, como uma estrutura definida pelo usuário, tem nenhum valor padrão válido.  
  
 Quando você usa um parâmetro de tipo para um parâmetro opcional, você deve assegurar-se de um tipo de referência para evitar a possibilidade de um tipo de valor com nenhum valor padrão válido. Isso significa que você deve restringir o parâmetro de tipo com o `Class` palavra-chave ou com o nome de uma classe específica.  
  
 **ID do erro:** BC32124  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Restringir o parâmetro de tipo para aceitar apenas um tipo de referência, ou não usá-lo para o parâmetro opcional.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Parâmetros opcionais](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)
