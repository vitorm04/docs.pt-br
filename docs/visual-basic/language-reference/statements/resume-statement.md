---
title: Instrução Resume (Visual Basic)
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
ms.openlocfilehash: 7b8c2e123c04ff9720d690507ee41a6b52f40c3f
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583269"
---
# <a name="resume-statement"></a>Instrução Resume
Retoma a execução após a conclusão de uma rotina de tratamento de erros.  
  
 Sugerimos que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as instruções `On Error` e `Resume`. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>Partes  
 `Resume`  
 Necessário. Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução será retomada na instrução última chamada para fora do procedimento que contém a rotina de tratamento de erros.  
  
 `Next`  
 Opcional. Se o erro ocorreu no mesmo procedimento que o manipulador de erros, a execução é retomada com a instrução imediatamente após a instrução que causou o erro. Se o erro ocorreu em um procedimento chamado, a execução será retomada com a instrução imediatamente após a instrução que a última chamada para fora do procedimento que contém a rotina de tratamento de erros (ou a instrução `On Error Resume Next`).  
  
 `line`  
 Opcional. A execução é retomada na linha especificada no argumento obrigatório `line`. O argumento `line` é um rótulo de linha ou número de linha e deve estar no mesmo procedimento que o manipulador de erro.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> É recomendável que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e as instruções `On Error` e `Resume`. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Se você usar uma instrução `Resume` em qualquer lugar diferente de em uma rotina de tratamento de erros, ocorrerá um erro.  
  
 A instrução `Resume` não pode ser usada em nenhum procedimento que contenha uma instrução `Try...Catch...Finally`.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a instrução `Resume` para encerrar o tratamento de erros em um procedimento e, em seguida, retomar a execução com a instrução que causou o erro. O número de erro 55 é gerado para ilustrar o uso da instrução `Resume`.  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)  
  
## <a name="see-also"></a>Consulte também

- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md)
- [Instrução On Error](../../../visual-basic/language-reference/statements/on-error-statement.md)
