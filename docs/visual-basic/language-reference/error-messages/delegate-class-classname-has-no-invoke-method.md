---
title: Classe Delegate '<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: e6ad06262806088347c94b3040b743618a3b3695
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874501"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Classe Delegate '\<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método

Uma chamada para `Invoke` por meio de um delegado falhou porque `Invoke` não está implementada na classe delegate.  
  
 **ID do erro:** BC30220  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Certifique-se de que uma instância da classe delegate tenha sido criada com uma `Dim` instrução e que um procedimento tenha sido atribuído à instância delegada com o `AddressOf` operador.  
  
2. Localize o código que implementa a classe delegada e verifique se ele implementa o `Invoke` procedimento.  
  
## <a name="see-also"></a>Confira também

- [Representantes](../../programming-guide/language-features/delegates/index.md)
- [Instrução Delegate](../statements/delegate-statement.md)
- [Operador AddressOf](../operators/addressof-operator.md)
- [Instrução Dim](../statements/dim-statement.md)
