---
title: Retomar Statement (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 853f3fe060b70c8a43957d3c843fb95539981679
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39296150"
---
# <a name="resume-statement"></a>Instrução Resume
Retoma a execução após a conclusão de uma rotina de tratamento de erros.  
  
 Sugerimos que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e o `On Error` e `Resume` instruções. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Partes  
 `Resume`  
 Necessário. Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução continuará na instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros.  
  
 `Next`  
 Opcional. Se o erro ocorreu no mesmo procedimento que o manipulador de erro, a execução continua com a instrução imediatamente após a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução é retomada com a instrução imediatamente após a instrução que pela última chamada do procedimento que contém a rotina de tratamento de erros (ou `On Error Resume Next` instrução).  
  
 `line`  
 Opcional. Retoma a execução na linha especificada em necessários `line` argumento. O `line` argumento é um rótulo de linha ou o número de linha e deve estar no mesmo procedimento que o manipulador de erro.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  É recomendável que você use o tratamento de exceções estruturado em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e o `On Error` e `Resume` instruções. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Se você usar um `Resume` declaração em qualquer lugar diferente de em uma rotina de tratamento de erro, um erro ocorre.  
  
 O `Resume` instrução não pode ser usada em qualquer procedimento que contém um `Try...Catch...Finally` instrução.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `Resume` instrução para terminar em um procedimento de tratamento de erros e, em seguida, retomar a execução com a instrução que causou o erro. Número do erro 55 é gerado para ilustrar o uso do `Resume` instrução.  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em VisualBasic)  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md)  
 [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
