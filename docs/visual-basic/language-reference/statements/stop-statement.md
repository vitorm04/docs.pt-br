---
title: "Instrução Stop (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Stop
helpviewer_keywords:
- breakpoints, Stop statements
- Stop statements [Visual Basic], syntax
- Stop statements [Visual Basic]
- execution [Visual Basic], suspending
- processing, interrupting
- processes, interrupting
- execution [Visual Basic], stopping
ms.assetid: c9a9fde0-d649-4662-9bef-bd0146ebc2a7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d4b7f04214234837a86bf0c77c0d7b6934e2babd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="stop-statement-visual-basic"></a>Instrução Stop (Visual Basic)
Suspende a execução.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Stop  
```  
  
## <a name="remarks"></a>Comentários  
 Você pode colocar `Stop` instruções em qualquer lugar em procedimentos para suspender a execução. Usando o `Stop` instrução é semelhante à configuração de um ponto de interrupção no código.  
  
 O `Stop` instrução suspende a execução, mas diferentemente `End`, ele não feche quaisquer arquivos ou desmarca todas as variáveis, a menos que ela seja encontrada em um arquivo executável compilado (.exe).  
  
> [!NOTE]
>  Se o `Stop` instrução for encontrada no código que está em execução fora do ambiente de desenvolvimento integrado (IDE), o depurador é invocado. Isso é verdadeiro independentemente se o código foi compilado no modo de depuração ou de varejo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Stop` instrução suspender a execução de cada iteração por meio de `For...Next` loop.  
  
 [!code-vb[VbVbalrStatements#56](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/stop-statement_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
