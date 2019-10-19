---
title: Instrução Erase (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 7dec2a859f664ee8dcbb305082ec33aeacbaccb4
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583395"
---
# <a name="erase-statement-visual-basic"></a>Instrução Erase (Visual Basic)
Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a>Partes  
 `arraylist`  
 Necessário. Lista de variáveis de matriz a serem apagadas. Várias variáveis são separadas por vírgulas.  
  
## <a name="remarks"></a>Comentários  
 A instrução `Erase` pode aparecer somente no nível do procedimento. Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou de módulo.  
  
 A instrução `Erase` é equivalente a atribuir `Nothing` a cada variável de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a instrução `Erase` para limpar duas matrizes e liberar sua memória (1000 e 100 elementos de armazenamento, respectivamente). Em seguida, a instrução `ReDim` atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Consulte também

- [Nothing](../../../visual-basic/language-reference/nothing.md)
- [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
