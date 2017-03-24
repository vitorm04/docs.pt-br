---
title: "&quot;&lt;typename&gt;&quot; é um tipo delegado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
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
ms.openlocfilehash: 3d6cc283f7e9815eb9b723a450731998f14b3424
ms.lasthandoff: 03/13/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a>'&lt;typename&gt;' é um tipo delegate
'\<typename >' é um tipo delegado. A construção Delegate permite somente uma única expressão AddressOf como uma lista de argumentos. Geralmente, uma expressão AddressOf pode ser usada em vez de uma construção delegate.  
  
 Um `New` cláusula criando uma instância de uma classe delegate fornece uma lista de argumentos inválido para o construtor delegado.  
  
 Você pode fornecer um único `AddressOf` expressão ao criar uma nova instância do delegado.  
  
 Esse erro pode resultar se você não passar argumentos ao construtor delegado, se você passar mais de um argumento, ou se você passar um argumento único que não é válido `AddressOf` expressão.  
  
 **ID do erro:** BC32008  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Usar um único `AddressOf` expressão na lista de argumentos para a classe delegate de `New` cláusula.  
  
## <a name="see-also"></a>Consulte também  
 [Novo operador](../../../visual-basic/language-reference/operators/new-operator.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)   
 [Como invocar um método delegado](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)
