---
title: "Declaração do operador deve ser um destes: +,-, *,-, -, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;= &gt;, &gt;=, CType, IsTrue, IsFalse | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
dev_langs:
- VB
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
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
ms.openlocfilehash: 197ff9f9509f6ed7d2bc098e529d34294f68df6e
ms.lasthandoff: 03/13/2017

---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a>Declaração do operador deve ser um destes: +,-, *,\,/, ^, &amp;, Like, Mod e, Or, Xor, não, &lt; &lt;, &gt; &gt;...
Você pode declarar somente um operador que está qualificado para a sobrecarga. A tabela a seguir lista os operadores que você pode declarar.  
  
|Tipo|Operadores|  
|----------|---------------|  
|Unário|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binário|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|Conversão (unário)|`CType`|  
  
 Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.  
  
 **ID do erro:** BC33000  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Selecione um operador de conjunto de operadores que pode ser sobrecarregados.  
  
2.  Se você precisar da funcionalidade de sobrecarregar um operador que você não pode sobrecarregar diretamente, crie uma `Function` procedimento que usa os parâmetros apropriados e retorna o valor apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Operator](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Como: definir um operador](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [Como: definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
