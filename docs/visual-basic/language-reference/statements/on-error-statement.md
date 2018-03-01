---
title: "Instrução On Error (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96baa5d91d0a600b84ed832fb1e3b1ed71a9d89d
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2018
---
# <a name="on-error-statement-visual-basic"></a>Instrução On Error (Visual Basic)
Ativa uma rotina de tratamento de erros e especifica o local da rotina de dentro de um procedimento; também pode ser usado para desabilitar uma rotina de tratamento de erros.  
  
 Sem tratamento de erros, qualquer erro de tempo de execução que ocorre é fatal: uma mensagem de erro é exibida e a execução é interrompida.  
  
 Sempre que possível, sugerimos que você use o tratamento em seu código, em vez de usar o tratamento de exceção não estruturado de exceções estruturado e `On Error` instrução. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  O `Error` palavra-chave também é usada a [instrução Error](../../../visual-basic/language-reference/statements/error-statement.md), que tem suporte para compatibilidade com versões anteriores.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`GoTo` `line`|Habilita a rotina de tratamento de erros que começa na linha especificada no necessários `line` argumento. O `line` argumento é qualquer rótulo de linha ou número de linha. Se ocorrer um erro de tempo de execução, controle as ramificações para a linha especificada, tornando o manipulador de erros ativa. A linha especificada deve estar no mesmo procedimento como a `On Error` instrução ou um erro de tempo de compilação ocorrerá.|  
|`GoTo` 0|Desabilita o manipulador de erros habilitados no procedimento atual e redefine-a para `Nothing`.|  
|`GoTo` -1|Desabilita exceções habilitadas no procedimento atual e redefine-a para `Nothing`.|  
|`Resume Next`|Especifica que, quando ocorre um erro de tempo de execução, controle passa para a instrução imediatamente após a instrução em que ocorreu o erro e continua a execução desse ponto. Use este formulário em vez de `On Error GoTo` ao acessar objetos.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Recomendamos que você use o tratamento estruturado de exceções em seu código sempre que possível, em vez de usar o tratamento de exceção não estruturados e `On Error` instrução. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Um manipulador de erro "enabled" é aquele que é ativado por uma `On Error` instrução. Um manipulador de erro "ativo" é um manipulador habilitado que está no processo de tratamento de erro.  
  
 Se ocorrer um erro enquanto um manipulador de erros está ativo (entre a ocorrência do erro e um `Resume`, `Exit Sub`, `Exit Function`, ou `Exit Property` instrução), o manipulador de erros do procedimento não pode tratar o erro. O controle retorna ao procedimento de chamada.  
  
 Se o procedimento de chamada tiver um manipulador de erros habilitado, ele será ativado para tratar o erro. Se o manipulador de erros do procedimento de chamada também estiver ativo, o controle passa através de chamada de procedimentos anteriores até encontra um manipulador de erros habilitado, porém inativa. Se tal nenhum manipulador de erro for encontrado, o erro é fatal no ponto em que ele realmente ocorreu.  
  
 Cada vez que o manipulador de erro passa o controle para um procedimento de chamada, esse procedimento se torna o procedimento atual. Depois que um erro é tratado por um manipulador de erro em qualquer procedimento, a execução é retomada no procedimento atual no ponto designado pelo `Resume` instrução.  
  
> [!NOTE]
>  Uma rotina de tratamento de erros não é um `Sub` procedimento ou uma `Function` procedimento. É uma seção de código marcado por um rótulo de linha ou um número de linha.  
  
## <a name="number-property"></a>Propriedade de número  
 Rotinas de tratamento de erros se baseiam no valor o `Number` propriedade o `Err` objeto para determinar a causa do erro. A rotina deve testar ou salvar os valores de propriedades relevantes na `Err` antes de qualquer outro erro pode ocorrer ou antes de um procedimento que pode causar um erro é chamado de objeto. Os valores de propriedades no `Err` objeto refletir apenas o erro mais recente. A mensagem de erro associada `Err.Number` está contida no `Err.Description`.  
  
## <a name="throw-statement"></a>Instrução Throw  
 Um erro que é gerado com o `Err.Raise` método define o `Exception` propriedade a uma instância recém-criada do <xref:System.Exception> classe. Para oferecer suporte ao aumento de exceções derivadas dos tipos de exceção, um `Throw` instrução tem suporte na linguagem. Isso leva a um único parâmetro que é a instância da exceção seja lançada. O exemplo a seguir mostra como esses recursos podem ser usados com a suporte à manipulação de exceção existente:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Observe que o `On Error GoTo` instrução intercepta todos os erros, independentemente da classe de exceção.  
  
## <a name="on-error-resume-next"></a>Houver erro, continuar  
 `On Error Resume Next`faz a execução continuar com a instrução imediatamente após a instrução que causou o erro de tempo de execução, ou com a instrução imediatamente após o mais recente de chamadas fora do procedimento que contém o `On Error Resume Next` instrução. Essa instrução permite a execução a continuar apesar de um erro de tempo de execução. Você pode colocar a rotina de tratamento de erros em que o erro ocorrer em vez de transferir o controle para outro local dentro do procedimento. Um `On Error Resume Next` instrução se torna inativa quando outro procedimento é chamado, portanto, você deve executar um `On Error Resume Next` instrução em cada chamada rotina se você quiser dentro da rotina de tratamento de erros embutidos.  
  
> [!NOTE]
>  O `On Error Resume Next` construção pode ser preferível `On Error GoTo` ao tratar erros gerados durante o acesso a outros objetos. Verificando `Err` após cada interação com um objeto remove ambiguidade sobre qual objeto foi acessado pelo código. Você pode ter certeza de qual objeto colocado o código de erro `Err.Number`, bem como de objeto que originalmente gerou o erro (o objeto especificado em `Err.Source`).  
  
## <a name="on-error-goto-0"></a>On Error GoTo 0  
 `On Error GoTo 0`desativa o tratamento de erro no procedimento atual. Ela não especifica a linha 0 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como 0. Sem um `On Error GoTo 0` instrução, um manipulador de erros é desativada automaticamente quando um procedimento é encerrado.  
  
## <a name="on-error-goto--1"></a>On Error GoTo -1  
 `On Error GoTo -1`Desabilita a exceção no procedimento atual. Ele não especificar uma linha -1 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como -1. Sem um `On Error GoTo -1` instrução, uma exceção é desativada automaticamente quando um procedimento é encerrado.  
  
 Para impedir que o código de tratamento de erros em execução quando nenhum erro ocorreu, coloque uma `Exit Sub`, `Exit Function`, ou `Exit Property` instrução imediatamente antes da rotina de tratamento de erros, como o fragmento a seguir:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Aqui, o código de tratamento de erros segue o `Exit Sub` instrução e precede o `End Sub` instrução para separá-lo do fluxo de procedimento. Você pode colocar o código de tratamento de erros em qualquer lugar em um procedimento.  
  
## <a name="untrapped-errors"></a>Erros não ajustados  
 Erros não ajustados em objetos são retornados para o aplicativo controlando quando o objeto está em execução como um arquivo executável. Dentro do ambiente de desenvolvimento não interceptados erros são retornados para o aplicativo de controle somente se as opções adequadas estão definidas. Consulte a documentação do aplicativo host para obter uma descrição dos quais opções devem ser definidas durante a depuração, como defini-las e se o host pode criar classes.  
  
 Se você criar um objeto que acessa outros objetos, você deve tentar manipular os erros não tratados que passam novamente. Se você não pode mapear os códigos de erro no `Err.Number` para um dos seus próprios erros e, em seguida, passe-los de volta para o chamador de seu objeto. Você deve especificar o erro adicionando o código de erro para o `VbObjectError` constante. Por exemplo, se o código de erro é 1052, atribuí-lo da seguinte maneira:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Erros de sistema durante as chamadas para bibliotecas de vínculo dinâmico (DLLs) do Windows não geram exceções e não podem ser ajustados com interceptação de erro do Visual Basic. Ao chamar funções DLL, você deve verificar cada valor de retorno de êxito ou falha (de acordo com as especificações de API) e em caso de falha, verifique o valor `Err` do objeto `LastDLLError` propriedade.  
  
## <a name="example"></a>Exemplo  
 Este primeiro exemplo usa o `On Error GoTo` instrução para especificar o local de uma rotina de tratamento de erros dentro de um procedimento. No exemplo, uma tentativa de dividir por zero gera o erro número 6. O erro é tratado na rotina de tratamento de erros e, em seguida, o controle é retornado para a instrução que causou o erro. O `On Error GoTo 0` instrução desativa a interceptação de erro. Em seguida, o `On Error Resume Next` instrução é usada para adiar a interceptação de erro para que o contexto para o erro gerado pela próxima instrução pode ser conhecido por determinados. Observe que `Err.Clear` é usado para limpar o `Err` propriedades do objeto após o erro é tratado.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## <a name="requirements"></a>Requisitos  
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library (em Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>  
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)  
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [Mensagens de Erro](../../../visual-basic/language-reference/error-messages/index.md)  
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
