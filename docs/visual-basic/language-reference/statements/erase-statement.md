---
title: Instrução Erase (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Instrução Erase (Visual Basic)
Usado para liberar variáveis de matriz e desalocar a memória usada para seus elementos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>Partes  
 `arraylist`  
 Necessário. Lista de variáveis de matriz a ser apagada. Diversas variáveis são separadas por vírgulas.  
  
## <a name="remarks"></a>Comentários  
 O `Erase` instrução pode aparecer somente no nível de procedimento. Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.  
  
 O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e liberar a memória (elementos de armazenamento 1000 e 100, respectivamente). O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
