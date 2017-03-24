---
title: "Não foi possível inferir argumentos de tipo do delegado | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
dev_langs:
- VB
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
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
ms.openlocfilehash: bb62156bdf3a6f8741e5d39ba7d671f13ec1a000
ms.lasthandoff: 03/13/2017

---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Não foi possível inferir argumentos de tipo a partir do delegado
Uma instrução de atribuição usa `AddressOf` para atribuir o endereço de um genérico procedimento para um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto não fornece informação suficiente para o compilador inferir os tipos, um erro será gerado.  
  
 **ID do erro:** BC36564  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Especificar os argumentos de tipo para o procedimento genérico de `AddressOf` expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)   
 [Lista de tipos](../../../visual-basic/language-reference/statements/type-list.md)   
 [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
