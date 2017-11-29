---
title: "Classe delegate &#39; &lt;classname&gt;&#39; não tem método Invoke, portanto uma expressão desse tipo não pode ser o destino de uma chamada de método"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Classe delegate &#39; &lt;classname&gt;&#39; não tem método Invoke, portanto uma expressão desse tipo não pode ser o destino de uma chamada de método
Uma chamada para `Invoke` através de um delegado falhou porque `Invoke` não está implementado na classe de delegado.  
  
 **ID do erro:** BC30220  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que uma instância da classe delegada foi criada com uma `Dim` instrução e que um procedimento foi designado para a instância delegada com o `AddressOf` operador.  
  
2.  Localize o código que implementa a classe delegada e certifique-se de que ele implementa o `Invoke` procedimento.  
  
## <a name="see-also"></a>Consulte também  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
