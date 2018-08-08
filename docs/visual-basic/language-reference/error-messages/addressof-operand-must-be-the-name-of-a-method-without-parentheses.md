---
title: '&#39;AddressOf&#39; operando deve ser o nome de um método (sem parênteses)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583806"
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; operando deve ser o nome de um método (sem parênteses)
O `AddressOf` operador cria uma instância de delegado de procedimento que faz referência a um procedimento específico. A sintaxe é a seguinte:  
  
 `AddressOf` `procedurename`  
  
 Você inseriu o seguinte argumento entre parênteses `AddressOf`, onde nenhuma é necessária.  
  
 **ID do erro:** BC30577  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remova os parênteses que delimitam o seguinte argumento `AddressOf`.  
  
2.  Verifique se que o argumento é um nome de método.  
  
## <a name="see-also"></a>Consulte também  
 [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
