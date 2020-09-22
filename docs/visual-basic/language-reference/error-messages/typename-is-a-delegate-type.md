---
title: "'<typename>' é um tipo delegado"
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 4cc0a1221dcf65aa2a16fd7d82568c8544f27fdb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875082"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename>' é um tipo delegado

' \<typename> ' é um tipo delegado. A construção delegate permite apenas uma única expressão AddressOf como uma lista de argumentos. Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.  
  
 Uma `New` cláusula que cria uma instância de uma classe delegate fornece uma lista de argumentos inválida para o construtor delegate.  
  
 Você pode fornecer apenas uma única `AddressOf` expressão ao criar uma nova instância de delegado.  
  
 Esse erro pode ocorrer se você não passar nenhum argumento para o construtor delegado, se você passar mais de um argumento, ou se você passar um único argumento que não seja uma expressão válida `AddressOf` .  
  
 **ID do erro:** BC32008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Use uma única `AddressOf` expressão na lista de argumentos para a classe delegate na `New` cláusula.  
  
## <a name="see-also"></a>Confira também

- [Novo operador](../operators/new-operator.md)
- [Operador AddressOf](../operators/addressof-operator.md)
- [Representantes](../../programming-guide/language-features/delegates/index.md)
- [Como invocar um método delegado](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
