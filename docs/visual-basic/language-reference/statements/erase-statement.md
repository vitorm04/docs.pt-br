---
title: Instrução Erase
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 6d2052ceccbecd772c4e4bb18052aed74223a36e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343696"
---
# <a name="erase-statement-visual-basic"></a>Instrução Erase (Visual Basic)
Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Partes  
 `arraylist`  
 Necessária. Lista de variáveis de matriz a serem apagadas. Várias variáveis são separadas por vírgulas.  
  
## <a name="remarks"></a>Comentários  
 A instrução `Erase` pode aparecer somente no nível do procedimento. Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou de módulo.  
  
 A instrução `Erase` é equivalente a atribuir `Nothing` a cada variável de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Erase` para limpar duas matrizes e liberar sua memória (1000 e 100 elementos de armazenamento, respectivamente). Em seguida, a instrução `ReDim` atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Consulte também

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
