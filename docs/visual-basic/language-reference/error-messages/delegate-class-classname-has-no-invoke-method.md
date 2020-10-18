---
title: Classe Delegate '<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 4e0fc61c7356008755134f670fa1fab0165cfd48
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162785"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>BC30220: a classe delegate ' \<classname> ' não tem um método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método

Uma chamada para `Invoke` por meio de um delegado falhou porque `Invoke` não está implementada na classe delegate.

 **ID do erro:** BC30220

## <a name="to-correct-this-error"></a>Para corrigir este erro

1. Certifique-se de que uma instância da classe delegate tenha sido criada com uma `Dim` instrução e que um procedimento tenha sido atribuído à instância delegada com o `AddressOf` operador.

2. Localize o código que implementa a classe delegada e verifique se ele implementa o `Invoke` procedimento.

## <a name="see-also"></a>Veja também

- [Representantes](../../programming-guide/language-features/delegates/index.md)
- [Instrução Delegate](../statements/delegate-statement.md)
- [Operador AddressOf](../operators/addressof-operator.md)
- [Instrução Dim](../statements/dim-statement.md)
