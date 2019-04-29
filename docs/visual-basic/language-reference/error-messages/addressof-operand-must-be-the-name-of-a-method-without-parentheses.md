---
title: O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: b8c67c2390df91c6a4af66e020365544e6bf369b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751625"
---
# <a name="addressof-operand-must-be-the-name-of-a-method-without-parentheses"></a>O operando 'AddressOf' deve ter o mesmo nome de um método (sem parênteses)
O `AddressOf` operador cria uma instância de procedimento delegado que faz referência a um procedimento específico. A sintaxe é da seguinte maneira.  
  
 `AddressOf` `procedurename`  
  
 Você inseriu o seguinte argumento entre parênteses `AddressOf`, em que nenhuma é necessária.  
  
 **ID do erro:** BC30577  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Remova os parênteses que delimitam o seguinte argumento `AddressOf`.  
  
2. Verifique se que o argumento é um nome de método.  
  
## <a name="see-also"></a>Consulte também

- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
