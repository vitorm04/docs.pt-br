---
title: '&#39;&lt;TypeName&gt; &#39; é um tipo delegado'
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: c6d4244ce72dedee50b65ba19978149ce86b9e87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595642"
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39;&lt;TypeName&gt; &#39; é um tipo delegado
'\<typename >' é um tipo delegado. A construção Delegate permite somente uma única expressão AddressOf como uma lista de argumentos. Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção de delegado.  
  
 Um `New` cláusula criando uma instância da classe delegada fornece uma lista de argumento inválido para construtor delegado.  
  
 Você pode fornecer um único `AddressOf` expressão ao criar uma nova instância de delegado.  
  
 Esse erro pode ocorrer se você não passar argumentos para construtor delegate, se você passar a mais de um argumento, ou se você passar um argumento único que não é válido `AddressOf` expressão.  
  
 **ID do erro:** BC32008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Usar um único `AddressOf` expressão na lista de argumentos para a classe delegate no `New` cláusula.  
  
## <a name="see-also"></a>Consulte também  
 [Operador New](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Como invocar um método delegado](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
