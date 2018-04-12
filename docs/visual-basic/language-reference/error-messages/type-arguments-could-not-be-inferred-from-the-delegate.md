---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Não foi possível inferir argumentos de tipo a partir do delegado
Usa uma instrução de atribuição `AddressOf` para atribuir o endereço de um generic procedimento como um delegado, mas não fornece nenhum argumento de tipo para o procedimento genérico.  
  
 Normalmente, quando você invoca um tipo genérico, você fornece um argumento de tipo para cada parâmetro de tipo que define o tipo genérico. Se você não fornecer nenhum argumento de tipo, o compilador tenta inferir os tipos a serem passados para os parâmetros de tipo. Se o contexto não fornece informações suficientes para o compilador inferir os tipos, um erro será gerado.  
  
 **ID do erro:** BC36564  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Especificar os argumentos de tipo para o procedimento genérico de `AddressOf` expressão.  
  
## <a name="see-also"></a>Consulte também  
 [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Procedimentos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Lista de Tipos](../../../visual-basic/language-reference/statements/type-list.md)  
 [Métodos de Extensão](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
