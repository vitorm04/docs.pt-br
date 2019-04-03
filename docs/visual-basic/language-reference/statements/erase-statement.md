---
title: Instrução Erase (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: bf3eb6476dc1485faeddab475f29e508175d3378
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840400"
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
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Consulte também

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
