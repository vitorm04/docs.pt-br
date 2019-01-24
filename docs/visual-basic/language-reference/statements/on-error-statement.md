---
title: Instrução On Error (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 9916c7197b260436a447a84b22df9b76dc5af4cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654874"
---
# <a name="on-error-statement-visual-basic"></a>Instrução On Error (Visual Basic)
Permite que uma rotina de tratamento de erros e especifica o local da rotina dentro de um procedimento; também pode ser usado para desabilitar uma rotina de tratamento de erros.  
  
 Sem tratamento de erro, qualquer erro de tempo de execução que ocorre é fatal: uma mensagem de erro é exibida e a execução é interrompida.  
  
 Sempre que possível, sugerimos que você use manipulação em seu código, em vez de usar o tratamento de exceção não estruturado de exceções estruturado e o `On Error` instrução. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  O `Error` palavra-chave também é usado em de [instrução Error](../../../visual-basic/language-reference/statements/error-statement.md), que tem suporte para compatibilidade com versões anteriores.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`GoTo` `line`|Permite que a rotina de tratamento de erros que começa na linha especificada em necessários `line` argumento. O `line` argumento é qualquer número de linha ou rótulo da linha. Se ocorrer um erro de tempo de execução, controle as ramificações para a linha especificada, tornando o manipulador de erro ativo. A linha especificada deve estar no mesmo procedimento que o `On Error` instrução ou um erro de tempo de compilação ocorrerá.|  
|`GoTo` 0|Desabilita o manipulador de erros habilitados no procedimento atual e redefine-o para `Nothing`.|  
|`GoTo` -1|Desabilita exceções habilitadas no procedimento atual e redefine-o para `Nothing`.|  
|`Resume Next`|Especifica que, quando ocorre um erro de tempo de execução, controle passa para a instrução imediatamente após a instrução em que ocorreu o erro e a execução continua a partir desse ponto. Use este formulário em vez de `On Error GoTo` ao acessar objetos.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  É recomendável que você use o tratamento de exceções estruturado em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e o `On Error` instrução. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Um manipulador de erro "enabled" é aquele que é ativado por um `On Error` instrução. Um manipulador de erro "ativo" é um manipulador habilitado que está no processo de tratamento de erro.  
  
 Se ocorrer um erro enquanto um manipulador de erros está ativo (entre a ocorrência do erro e uma `Resume`, `Exit Sub`, `Exit Function`, ou `Exit Property` instrução), o manipulador de erros do procedimento atual não pode tratar o erro. O controle retorna para o procedimento de chamada.  
  
 Se o procedimento de chamada tem um manipulador de erros habilitado, ele será ativado para lidar com o erro. Se o manipulador de erros do procedimento de chamada também estiver ativo, o controle passa através de chamada de procedimentos anteriores até encontra um manipulador de erros habilitado, porém inativa. Se nenhum manipulador erro for encontrado, o erro é fatal no ponto em que ele realmente ocorreu.  
  
 Cada vez que o manipulador de erro passa o controle volta para um procedimento de chamada, esse procedimento torna-se o procedimento atual. Depois que um erro é tratado por um manipulador de erro em qualquer procedimento, a execução é retomada no procedimento atual no ponto designado pelo `Resume` instrução.  
  
> [!NOTE]
>  Uma rotina de tratamento de erro não é um `Sub` procedimento ou uma `Function` procedimento. É uma seção de código marcado por um rótulo ou um número de linha.  
  
## <a name="number-property"></a>Propriedade de número  
 Rotinas de tratamento de erros se baseiam no valor da `Number` propriedade do `Err` objeto para determinar a causa do erro. A rotina deve testar ou salvar os valores de propriedade relevante no `Err` antes de qualquer outro erro pode ocorrer ou antes de um procedimento que pode causar um erro é chamado de objeto. Os valores de propriedades no `Err` objeto refletir somente o erro mais recente. A mensagem de erro associada `Err.Number` está contida no `Err.Description`.  
  
## <a name="throw-statement"></a>Instrução Throw  
 Um erro que é gerado com o `Err.Raise` método define o `Exception` propriedade para uma instância recém-criada do <xref:System.Exception> classe. Para dar suporte a gerar exceções derivadas dos tipos de exceção, um `Throw` instrução tem suporte na linguagem. Isso leva um único parâmetro que é a instância de exceção seja lançada. O exemplo a seguir mostra como esses recursos podem ser usados com a suporte de manipulação de exceção existente:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Observe que o `On Error GoTo` instrução intercepta todos os erros, independentemente da classe de exceção.  
  
## <a name="on-error-resume-next"></a>On Error Resume em seguida  
 `On Error Resume Next` faz a execução continuar com a instrução imediatamente após a instrução que causou o erro de tempo de execução ou com a instrução imediatamente após a mais recente chamada fora do procedimento que contém o `On Error Resume Next` instrução. Essa instrução permite que a execução continue, apesar de um erro de tempo de execução. Você pode colocar a rotina de tratamento de erros em que o erro ocorreria em vez de transferir o controle para outro local dentro do procedimento. Uma `On Error Resume Next` instrução se torna inativa quando outro procedimento é chamado, portanto, você deve executar um `On Error Resume Next` instrução em cada chamada de rotina se você quiser dentro dessa rotina de tratamento de erros embutidos.  
  
> [!NOTE]
>  O `On Error Resume Next` construção pode ser preferível `On Error GoTo` ao tratar erros gerados durante o acesso a outros objetos. Verificando `Err` após cada interação com um objeto remove a ambiguidade sobre qual objeto foi acessado pelo código. Você pode ter certeza qual objeto colocado o código de erro `Err.Number`, bem como qual objeto originalmente gerou o erro (o objeto especificado no `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0` desativa o tratamento de erro no procedimento atual. Ela não especifica a linha 0 como o início do código de tratamento de erros, mesmo se o procedimento contém uma linha numerada como 0. Sem um `On Error GoTo 0` instrução, um manipulador de erro é desativada automaticamente quando um procedimento é encerrado.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1` Desabilita a exceção no procedimento atual. Ele não especificar uma linha -1 como o início do código de tratamento de erros, mesmo se o procedimento contém uma linha numerada como -1. Sem um `On Error GoTo -1` instrução, uma exceção é desativada automaticamente quando um procedimento é encerrado.  
  
 Para impedir que o código de tratamento de erros em execução quando nenhum erro tiver ocorrido, coloque um `Exit Sub`, `Exit Function`, ou `Exit Property` instrução imediatamente antes da rotina de tratamento de erros, como no seguinte fragmento:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Aqui, o código de tratamento de erro segue o `Exit Sub` instrução e precede o `End Sub` instrução para separá-lo do fluxo do procedimento. Você pode colocar o código de tratamento de erros em qualquer lugar em um procedimento.  
  
## <a name="untrapped-errors"></a>Erros não interceptados  
 Erros não interceptados em objetos são retornados para o aplicativo de controle quando o objeto é executado como um arquivo executável. Dentro do ambiente de desenvolvimento, não interceptados erros são retornados para o aplicativo de controle somente se as opções adequadas estão definidas. Consulte a documentação do seu aplicativo de host para obter uma descrição dos quais opções devem ser definidas durante a depuração, como defini-las e se o host pode criar classes.  
  
 Se você criar um objeto que acessa outros objetos, você deve tentar tratar os erros sem tratamento que passam de volta. Se você não pode mapear os códigos de erro no `Err.Number` para um dos seus próprios erros e, em seguida, passe-os de volta para o chamador de seu objeto. Você deve especificar seu erro ao adicionar seu código de erro para o `VbObjectError` constante. Por exemplo, se seu código de erro é 1052, atribuí-lo da seguinte maneira:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Erros do sistema durante as chamadas para bibliotecas de vínculo dinâmico (DLLs) do Windows não geram exceções e não podem ser interceptados com a interceptação de erros do Visual Basic. Ao chamar funções de DLL, você deve verificar cada valor de retorno de êxito ou falha (de acordo com as especificações de API) e em caso de falha, verifique o valor `Err` do objeto `LastDLLError` propriedade.  
  
## <a name="example"></a>Exemplo  
 Este primeiro exemplo usa o `On Error GoTo` instrução para especificar o local de uma rotina de tratamento de erros dentro de um procedimento. No exemplo, uma tentativa de dividir por zero gera o erro número 6. O erro é tratado na rotina de tratamento de erros e controle, em seguida, retorne para a instrução que causou o erro. O `On Error GoTo 0` instrução desativa a interceptação de erro. Em seguida, a `On Error Resume Next` instrução é usada para adiar a interceptação de erros para que o contexto para o erro gerado pela próxima instrução pode ser conhecido para determinados. Observe que `Err.Clear` é usado para limpar o `Err` propriedades do objeto depois que o erro é tratado.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)
- [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)
- [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)
- [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
