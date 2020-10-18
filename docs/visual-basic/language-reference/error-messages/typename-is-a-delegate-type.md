---
title: "'<typename>' é um tipo delegado"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: dcb52188c53b38ac14de0002b5212bb33c9f7203
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161771"
---
# <a name="bc32008-typename-is-a-delegate-type"></a>BC32008: ' \<typename> ' é um tipo delegado

' \<typename> ' é um tipo delegado. A construção delegate permite apenas uma única expressão AddressOf como uma lista de argumentos. Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.

 Uma `New` cláusula que cria uma instância de uma classe delegate fornece uma lista de argumentos inválida para o construtor delegate.

 Você pode fornecer apenas uma única `AddressOf` expressão ao criar uma nova instância de delegado.

 Esse erro pode ocorrer se você não passar nenhum argumento para o construtor delegado, se você passar mais de um argumento, ou se você passar um único argumento que não seja uma expressão válida `AddressOf` .

 **ID do erro:** BC32008

## <a name="to-correct-this-error"></a>Para corrigir este erro

- Use uma única `AddressOf` expressão na lista de argumentos para a classe delegate na `New` cláusula.

## <a name="see-also"></a>Veja também

- [Novo operador](../operators/new-operator.md)
- [Operador AddressOf](../operators/addressof-operator.md)
- [Representantes](../../programming-guide/language-features/delegates/index.md)
- [Como invocar um método delegado](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
