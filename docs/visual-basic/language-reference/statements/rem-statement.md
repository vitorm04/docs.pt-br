---
title: "Instrução REM (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
dev_langs:
- VB
helpviewer_keywords:
- REM statement
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 47e6d1195a7c2ccba9c1e054b216177792f8b2e9
ms.lasthandoff: 03/13/2017

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
 Você pode colocar um `REM` instrução sozinha em uma linha, ou você pode colocá-lo em uma linha após outra instrução. O `REM` instrução deve ser a última instrução na linha. Se ela segue outra instrução, o `REM` deve ser separada dessa instrução por um espaço.  
  
 Você pode usar aspas simples (`'`) em vez de `REM`. Isso é verdadeiro se o seu comentário segue outra instrução na mesma linha ou fica sozinho em uma linha.  
  
> [!NOTE]
>  Você não pode continuar uma `REM` instrução usando uma sequência de continuação de linha (`_`). Quando um comentário começa, o compilador não examina os caracteres para um significado especial. Para um comentário de várias linhas, use outra `REM` instrução ou um símbolo de comentário (`'`) em cada linha.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra o `REM` instrução, que é usada para incluir comentários explicativos em um programa. Ele também mostra a alternativa de usar o caractere de aspas simples (`'`) em vez de `REM`.  
  
 [!code-vb[VbVbalrStatements n º&6;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/rem-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Comentários no código](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)   
 [Como quebrar e combinar instruções no código](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
