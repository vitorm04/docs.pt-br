---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 51b0bbf2e346acdd84a1bc2283db4a71adc9f7dc
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870424"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Não foi possível inferir argumentos de tipo a partir do delegado

Uma instrução de atribuição usa `AddressOf` para atribuir o endereço de um procedimento genérico a um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que o tipo genérico define. Se você não fornecer nenhum argumento de tipo, o compilador tentará inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto não fornecer informações suficientes para que o compilador inferir os tipos, um erro será gerado.  
  
 **ID do erro:** BC36564  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Especifique os argumentos de tipo para o procedimento genérico na `AddressOf` expressão.  
  
## <a name="see-also"></a>Confira também

- [Tipos genéricos no Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Operador AddressOf](../operators/addressof-operator.md)
- [Procedimentos genéricos no Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Lista de Tipos](../statements/type-list.md)
- [Métodos de Extensão](../../programming-guide/language-features/procedures/extension-methods.md)
