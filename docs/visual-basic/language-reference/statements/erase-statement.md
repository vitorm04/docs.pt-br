---
title: "Instrução Erase (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
dev_langs:
- VB
helpviewer_keywords:
- Erase keyword
- Erase statement
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
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
ms.openlocfilehash: d9b491b3149f3753722e7126a00d618cfc7a47d1
ms.lasthandoff: 03/13/2017

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
 O `Erase` declaração pode aparecer somente no nível de procedimento. Isso significa que você pode liberar matrizes dentro de um procedimento, mas não no nível de classe ou módulo.  
  
 O `Erase` instrução é equivalente ao atribuir `Nothing` para cada variável de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Erase` instrução para limpar duas matrizes e liberar seu memória (elementos de armazenamento 1000 e 100, respectivamente). O `ReDim` instrução, em seguida, atribui uma nova instância de matriz à matriz tridimensional.  
  
 [!code-vb[19 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Nada](../../../visual-basic/language-reference/nothing.md)   
 [Instrução ReDim](../../../visual-basic/language-reference/statements/redim-statement.md)
