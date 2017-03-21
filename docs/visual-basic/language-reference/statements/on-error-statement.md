---
title: "Instrução On Error (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.OnError
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement, On Error
- control flow, branching
- Error keyword
- execution, conditional
- Resume statement, and On Error statement
- Error statement, and On Error statement
- GoTo statement, and On Error statement
- branching, on error
- conditional statements, On Error
- On Error statement, syntax
- On keyword
- run-time errors, handling
- On Error statement
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 22
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
ms.openlocfilehash: a5b14d1eb5ee5bc28bb685e098c38adb88f847d8
ms.lasthandoff: 03/13/2017

---
# <a name="on-error-statement-visual-basic"></a>Instrução On Error (Visual Basic)
Ativa uma rotina de tratamento de erros e especifica o local da rotina de dentro de um procedimento; também pode ser usado para desabilitar uma rotina de tratamento de erros.  
  
 Sem um `On Error` instrução, qualquer erro de tempo de execução que ocorre é fatal: uma mensagem de erro é exibida e a execução é interrompida.  
  
 Sempre que possível, sugerimos que você use tratamento em seu código, em vez de usar o tratamento de exceção não estruturado de exceções estruturado e o `On Error` instrução. Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  O `Error` palavra-chave também é usada a [instrução Error](../../../visual-basic/language-reference/statements/error-statement.md), que tem suporte para compatibilidade com versões anteriores.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`GoTo` `line`|Permite que a rotina de tratamento de erros começa na linha especificada conforme exigido `line` argumento. O `line` é qualquer número de linha ou rótulo da linha. Se ocorrer um erro de tempo de execução, controle as ramificações para a linha especificada, tornando o manipulador de erros ativa. A linha especificada deve estar no mesmo procedimento que o `On Error` instrução ou um erro de tempo de compilação ocorrerá.|  
|`GoTo` 0|Desabilita o manipulador de erros do procedimento atual e redefine a `Nothing`.|  
|`GoTo` -1|Desabilita a exceção habilitada no procedimento atual e redefine a `Nothing`.|  
|`Resume Next`|Especifica que, quando ocorre um erro de tempo de execução, controle passa para a instrução imediatamente após a instrução onde ocorreu o erro e continua a execução desse ponto. Use este formulário em vez de `On Error GoTo` ao acessar objetos.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  É recomendável que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturado e o `On Error` instrução. Para obter mais informações, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Um manipulador de erro "enabled" é aquele que é ativado por um `On Error` instrução. Um manipulador de erro "ativos" é um manipulador habilitado que está no processo de tratamento de erro.  
  
 Se ocorrer um erro enquanto um manipulador de erros está ativo (entre a ocorrência do erro e um `Resume`, `Exit Sub`, `Exit Function`, ou `Exit Property` instrução), o manipulador de erros do procedimento atual não pode manipular o erro. O controle retorna para o procedimento de chamada.  
  
 Se o procedimento de chamada tem um manipulador de erros ativada, ele será ativado para manipular o erro. Se o manipulador de erros do procedimento de chamada também estiver ativo, o controle passa através de procedimentos chamados anteriores até que seja encontrado um manipulador de erro habilitado mas inativo. Se nenhum manipulador de erro tal for encontrado, o erro é fatal no ponto em que ele realmente ocorreu.  
  
 Cada vez que o manipulador de erro passa o controle para um procedimento de chamada, esse procedimento torna-se o procedimento atual. Quando um erro é tratado por um manipulador de erro em qualquer procedimento, a execução é retomada no procedimento atual no ponto designado a `Resume` instrução.  
  
> [!NOTE]
>  Uma rotina de tratamento de erros não é um `Sub` procedimento ou uma `Function` procedimento. É uma seção de código marcado por um rótulo ou um número de linha.  
  
## <a name="number-property"></a>Propriedade Number  
 Rotinas de tratamento de erros se baseiam no valor o `Number` propriedade o `Err` objeto para determinar a causa do erro. A rotina deve testar ou salvar valores de propriedades relevantes no `Err` antes de qualquer outro erro pode ocorrer ou antes de um procedimento que pode causar um erro é chamado de objeto. Os valores de propriedades no `Err` objeto refletir somente o erro mais recente. A mensagem de erro associada `Err.Number` está contida no `Err.Description`.  
  
## <a name="throw-statement"></a>Instrução Throw  
 Um erro é gerado com o `Err.Raise` método define o `Exception` propriedade a uma instância recém-criado da <xref:System.Exception>classe.</xref:System.Exception> Para suportar o aumento de exceções derivadas dos tipos de exceção, um `Throw` instrução é suportada na linguagem. Isso usa um único parâmetro que é a instância da exceção seja lançada. O exemplo a seguir mostra como esses recursos podem ser usados com a suporte de manipulação de exceção existente:  
  
 [!code-vb[17 VbVbalrErrorHandling](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Observe que o `On Error GoTo` instrução intercepta todos os erros, independentemente da classe de exceção.  
  
## <a name="on-error-resume-next"></a>Houver erro, continuar  
 `On Error Resume Next`faz a execução continuar com a instrução imediatamente após a instrução que causou o erro de tempo de execução ou com a instrução imediatamente após o mais recente de chamadas fora do procedimento que contém o `On Error Resume Next` instrução. Essa instrução permite continuar apesar de um erro de tempo de execução da execução. Você pode colocar a rotina de tratamento de erros onde ocorre o erro em vez de transferir o controle para outro local dentro do procedimento. Um `On Error Resume Next` instrução se torna inativa quando outro procedimento é chamado, portanto você deve executar um `On Error Resume Next` instrução em cada chamada rotina se desejar dentro dessa rotina de tratamento de erros de embutido.  
  
> [!NOTE]
>  O `On Error Resume Next` construção pode ser preferível `On Error GoTo` ao tratamento de erros gerados durante o acesso a outros objetos. Verificando `Err` após cada interação com um objeto remove a ambiguidade sobre qual objeto foi acessado pelo código. Você pode ter certeza qual objeto colocado o código de erro `Err.Number`, bem como qual objeto originalmente gerou o erro (o objeto especificado em `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0`desativa o tratamento de erros no procedimento atual. Ela não especifica a linha 0 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como 0. Sem um `On Error GoTo 0` instrução, um manipulador de erro é desabilitada automaticamente quando um procedimento é encerrado.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1`Desabilita a exceção do procedimento atual. Ele não especificar uma linha -1 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como -1. Sem um `On Error GoTo -1` instrução, uma exceção é desativada automaticamente quando um procedimento é encerrado.  
  
 Para impedir que o código de tratamento de erros em execução quando nenhum erro ocorreu, coloque uma `Exit Sub`, `Exit Function`, ou `Exit Property` instrução imediatamente antes da rotina de tratamento de erros, como o fragmento a seguir:  
  
 [!code-vb[VbVbalrErrorHandling n º&18;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Aqui, o código de tratamento de erros segue o `Exit Sub` instrução e precede o `End Sub` instrução para separá-lo do fluxo de procedimento. Você pode colocar código de tratamento de erros em qualquer lugar em um procedimento.  
  
## <a name="untrapped-errors"></a>Erros não ajustados  
 Erros não ajustados em objetos são retornados para o aplicativo de controle quando o objeto é executado como um arquivo executável. No ambiente de desenvolvimento, não interceptados erros são retornados para o aplicativo de controle somente se as opções apropriadas estão definidas. Consulte a documentação do aplicativo host para obter uma descrição dos quais opções devem ser definidas durante a depuração, como configurá-las e se o host pode criar classes.  
  
 Se você criar um objeto que acessa outros objetos, você deve tentar manipular os erros não tratados que passam novamente. Se você não pode mapear os códigos de erro no `Err.Number` um dos seus próprios erros e em seguida, transferi-los novamente para o chamador de seu objeto. Você deve especificar o erro adicionando o código de erro para o `VbObjectError` constante. Por exemplo, se seu código de erro é 1052, atribua-lo da seguinte maneira:  
  
 [!code-vb[19 VbVbalrErrorHandling](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Erros de sistema durante as chamadas para bibliotecas de vínculo dinâmico (DLLs) do Windows não acione exceções e não podem ser interceptados com a interceptação de erros do Visual Basic. Ao chamar funções DLL, você deve verificar cada valor de retorno de êxito ou falha (de acordo com as especificações de API) e em caso de falha, verifique o valor `Err` do objeto `LastDLLError` propriedade.  
  
## <a name="example"></a>Exemplo  
 Este primeiro exemplo usa o `On Error GoTo` para especificar o local de uma rotina de tratamento de erros dentro de um procedimento. No exemplo, uma tentativa de divisão por zero gera erro número 6. O erro é tratado da rotina de tratamento de erros e controle, em seguida, retorne para a instrução que causou o erro. O `On Error GoTo 0` instrução desativa a interceptação de erro. O `On Error Resume Next` instrução é usada para adiar a interceptação de erros para que o contexto para o erro gerado pela próxima instrução pode ser conhecido por determinados. Observe que `Err.Clear` é usado para limpar o `Err` propriedades do objeto depois que o erro é tratado.  
  
 [!code-vb[20 VbVbalrErrorHandling](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** biblioteca de tempo de execução do Visual Basic (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.Err%2A></xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A></xref:Microsoft.VisualBasic.ErrObject.Number%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A></xref:Microsoft.VisualBasic.ErrObject.Description%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A></xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Mensagens de erro](../../../visual-basic/language-reference/error-messages/index.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
