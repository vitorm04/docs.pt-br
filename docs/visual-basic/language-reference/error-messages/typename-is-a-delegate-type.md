---
title: '&#39;&lt;TypeName&gt; &#39; é um tipo delegado'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 6676328d0c1ea459f5934b5f9e2cb66580adad40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737196"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;TypeName&gt; &#39; é um tipo delegado
'\<typename >' é um tipo delegado. A construção Delegate permite apenas uma única expressão AddressOf como uma lista de argumentos. Geralmente, uma expressão de AddressOf pode ser usada em vez de uma construção de delegado.  
  
 Um `New` cláusula criando uma instância de uma classe de representante fornece uma lista de argumentos inválida para o construtor do delegado.  
  
 Você pode fornecer um único `AddressOf` expressão durante a criação de uma nova instância de delegado.  
  
 Esse erro pode resultar se você não passar argumentos para o construtor delegado, se você passar mais de um argumento ou se você passar um argumento único que não é válido `AddressOf` expressão.  
  
 **ID do erro:** BC32008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Usar uma única `AddressOf` expressão na lista de argumentos para a classe de delegado no `New` cláusula.  
  
## <a name="see-also"></a>Consulte também
- [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Como: Invocar um método delegado](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
