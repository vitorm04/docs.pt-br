---
title: "Instrução REM (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d64ce970e3e74437f5e8c63c8a4d578900902192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="rem-statement-visual-basic"></a>Instrução REM (Visual Basic)
Usado para incluir comentários explicativos no código-fonte de um programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>Partes  
 `comment`  
 Opcional. O texto de qualquer comentário que você deseja incluir. Um espaço é necessário entre a `REM` palavra-chave e `comment`.  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar um `REM` instrução sozinha em uma linha, ou você pode colocá-lo em uma linha após outra instrução. O `REM` instrução deve ser a última instrução na linha. Se ela segue outra instrução, o `REM` devem ser separados dessa instrução por um espaço.  
  
 Você pode usar aspas simples (`'`) em vez de `REM`. Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.  
  
> [!NOTE]
>  Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha (`_`). Quando um comentário começa, o compilador não examina os caracteres para um significado especial. Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário (`'`) em cada linha.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o `REM` instrução, que é usada para incluir comentários explicativos em um programa. Ele também mostra a possibilidade de usar o caractere de aspas simples (`'`) em vez de `REM`.  
  
 [!code-vb[VbVbalrStatements#6](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Comentários no Código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
