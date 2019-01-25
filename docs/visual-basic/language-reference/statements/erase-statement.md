---
title: Instrução Erase (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: cab3da4465b4671d203036c2d9bcd40662dc234a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522434"
---
# <a name="erase-statement-visual-basic"></a>Instrução Erase (Visual Basic)
Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Partes  
 `arraylist`  
 Necessário. Lista de variáveis de matriz a ser apagado. Diversas variáveis são separadas por vírgulas.  
  
## <a name="remarks"></a>Comentários  
 O `Erase` declaração pode aparecer somente no nível de procedimento. Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.  
  
 O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e sua memória livre (1000 e 100 elementos de armazenamento, respectivamente). O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
