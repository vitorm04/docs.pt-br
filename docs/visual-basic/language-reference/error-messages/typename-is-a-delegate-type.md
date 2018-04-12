---
title: '&#39; &lt;typename&gt;&#39; é um tipo delegado'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9428f0ac321b90e36d4d987381ed69b6c968894c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>&#39; &lt;typename&gt;&#39; é um tipo delegado
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
