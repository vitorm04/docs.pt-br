---
title: "Instrução Resume | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
dev_langs:
- VB
helpviewer_keywords:
- Next statement, Resume
- Resume Next statement
- execution, resuming
- run-time errors, resuming after
- Resume statement, syntax
- errors [Visual Basic], resuming after
- Error statement, and Resume statement
- execution
- Resume statement
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: 16
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
ms.openlocfilehash: e1ba64bdfb6bc34e463ce000f7541c520a92520b
ms.lasthandoff: 03/13/2017

---
# <a name="resume-statement"></a>Instrução Resume
Retoma a execução após a conclusão de uma rotina de tratamento de erros.  
  
 Sugerimos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturado e o `On Error` e `Resume` instruções. Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Partes  
 `Resume`  
 Necessário. Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução é retomada na instrução de última chamada do procedimento que contém a rotina de tratamento de erros.  
  
 `Next`  
 Opcional. Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução imediatamente após a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução continua com a instrução imediatamente após a instrução que a última chamada do procedimento que contém a rotina de tratamento de erros (ou `On Error Resume Next` instrução).  
  
 `line`  
 Opcional. A execução é retomada na linha especificada conforme exigido `line` argumento. O `line` argumento é um número da linha ou rótulo da linha e deve estar no mesmo procedimento que o manipulador de erro.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  É recomendável que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturado e o `On Error` e `Resume` instruções. Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Se você usar um `Resume` declaração em qualquer local diferente em uma rotina de tratamento de erros, um erro ocorre.  
  
 O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Resume` instrução para terminar em um procedimento de tratamento de erros e, em seguida, continuar a execução com a instrução que causou o erro. Número do erro 55 é gerado para ilustrar o uso do `Resume` instrução.  
  
 [!code-vb[VbVbalrErrorHandling n º&16;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md)   
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
