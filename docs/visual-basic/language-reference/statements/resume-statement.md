---
title: "Instrução Resume"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a>Instrução Resume
Retoma a execução após a conclusão de uma rotina de tratamento de erros.  
  
 Sugerimos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e `On Error` e `Resume` instruções. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Partes  
 `Resume`  
 Necessário. Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução continua com a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, retoma a execução na instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros.  
  
 `Next`  
 Opcional. Se o erro ocorreu no mesmo procedimento como o manipulador de erro, a execução continua com a instrução imediatamente após a instrução que causou o erro. Se o erro ocorreu em um procedimento de chamada, a execução continua com a instrução imediatamente após a instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros (ou `On Error Resume Next` instrução).  
  
 `line`  
 Opcional. Retoma a execução na linha especificada no necessários `line` argumento. O `line` argumento é um rótulo de linha ou um número de linha e deve estar no mesmo procedimento que o manipulador de erro.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Recomendamos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e `On Error` e `Resume` instruções. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Se você usar um `Resume` declaração em qualquer lugar diferente em uma rotina de tratamento de erros, um erro ocorre.  
  
 O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Resume` instrução terminar em um procedimento de tratamento de erros e, em seguida, retomar a execução com a instrução que causou o erro. Número do erro 55 é gerado para ilustrar o uso de `Resume` instrução.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md)  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
