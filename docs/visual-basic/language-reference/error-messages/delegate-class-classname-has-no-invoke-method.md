---
title: "Delegar a classe&lt;classname&gt;&quot; não tem nenhum método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: 10
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: ddc5ef0f0b3e9baa58f17dafb727e250c0fba9fd
ms.lasthandoff: 03/13/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Delegar a classe&lt;classname&gt;' não tem nenhum método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
Uma chamada para `Invoke` através de um delegado falhou porque `Invoke` não está implementado na classe de delegado.  
  
 **ID do erro:** BC30220  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que uma instância da classe delegada foi criada com uma `Dim` de instrução e que um procedimento foi designado para o exemplo delegado com o `AddressOf` operador.  
  
2.  Localize o código que implementa a classe delegada e certifique-se de que ela implemente o `Invoke` procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Instrução delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
