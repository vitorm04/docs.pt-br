---
title: Não foi possível inferir argumentos de tipo a partir do delegado
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: 757483f1e88276dd9db82de1c2a7e47b5c975b0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
