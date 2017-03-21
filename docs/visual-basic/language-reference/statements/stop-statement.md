---
title: "Instrução Stop (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Stop
dev_langs:
- VB
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements, syntax
- Stop statements
- execution, suspending
- processing, interrupting
- processes, interrupting
- execution, stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
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
ms.openlocfilehash: 9735ad3e3758b2c2f7922dd2f85ea3e23a8be3d0
ms.lasthandoff: 03/13/2017

---
# <a name="stop-statement-visual-basic"></a>Instrução Stop (Visual Basic)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `Stop` instruções em qualquer lugar nos procedimentos para suspender a execução. Usando o `Stop` instrução é semelhante à configuração de um ponto de interrupção no código.  
  
 O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não fecha os arquivos nem desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
> [!NOTE]
>  Se o `Stop` declaração é encontrada no código que está em execução fora do ambiente de desenvolvimento integrado (IDE), o depurador é invocado. Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Stop` instrução para suspender a execução de cada iteração por meio de `For...Next` loop.  
  
 [!code-vb[56 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
