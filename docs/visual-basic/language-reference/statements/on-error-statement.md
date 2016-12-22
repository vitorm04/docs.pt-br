---
title: "Instru&#231;&#227;o On Error (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.OnError"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ramificação, em erro"
  - "Instruções condicionais, Em erro"
  - "fluxo de controle, ramificação"
  - "tratamento de erros, instrução On Error"
  - "palavra-chave Error"
  - "instrução Error, e instrução On Error"
  - "erros [Visual Basic], trapping"
  - "execução, conditional"
  - "Instrução GoTo, e instrução On Error"
  - "Próxima instrução, Em erro"
  - "instrução On Error"
  - "instrução On Error, sintaxe"
  - "palavra-chave On"
  - "instrução Resume Next"
  - "instrução Resume, e instrução On Error"
  - "erros de tempo de execução, tratamento"
  - "código do Visual Basic, fluxo de controle"
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Instru&#231;&#227;o On Error (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ativa uma rotina de tratamento de erros e especifica o local da rotina dentro de um procedimento; também pode ser usado para desativar uma rotina de tratamento de erros.  
  
 Sem um `On Error` instrução, qualquer erro de tempo de execução que ocorre é fatal: é apresentada uma mensagem de erro e pára a execução.  
  
 Sempre que possível, sugerimos que você use o tratamento em seu código, em vez de usar o tratamento de exceção não estruturada de exceção estruturada e o `On Error` instrução.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  O `Error` palavra\-chave também é usada a [Instrução Error](../../../visual-basic/language-reference/statements/error-statement.md), que tem suporte para compatibilidade com versões anteriores.  
  
## Sintaxe  
  
```  
On Error { GoTo [ line | 0 | -1 ] | Resume Next }  
```  
  
## Partes  
  
|||  
|-|-|  
|Termo|Definição|  
|`GoTo` `line`|Permite que a rotina de tratamento de erros começa na linha especificada nas caixas necessário `line` argumento.  O `line` argumento é qualquer rótulo de linha ou o número da linha.  Se ocorrer um erro de tempo de execução, controle as ramificações para a linha especificada, tornando o manipulador de erro ativo.  A linha especificada deve estar no mesmo procedimento como o `On Error` erro de tempo de compilação ou a instrução ocorrerá.|  
|`GoTo` 0|Desativa o tratamento de erros ativada no procedimento atual e redefine para `Nothing`.|  
|`GoTo` \-1|Desativa a exceção habilitada no procedimento atual e redefine para `Nothing`.|  
|`Resume Next`|Especifica que, quando ocorre um erro de tempo de execução, controle vai para a declaração imediatamente seguinte a instrução em que ocorreu o erro e continua de execução a partir desse ponto.  Use este formulário em vez de `On Error GoTo` quando o acesso a objetos.|  
  
## Comentários  
  
> [!NOTE]
>  Recomendamos que você use manipulação de exceção estruturada no seu código sempre que possível, em vez de usar o tratamento de exceção não estruturada e o `On Error` instrução.  Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Um manipulador de erro "enabled" é aquele que é ativado por um `On Error` instrução.  Um manipulador de erro "ativo" é um manipulador habilitado que está no processo de tratamento de erro.  
  
 Se ocorrer um erro enquanto um manipulador de erro está ativo \(entre a ocorrência do erro e uma `Resume`, `Exit Sub`, `Exit Function`, ou `Exit Property` instrução\), tratamento de erros do procedimento atual não é possível manipular o erro.  O controle retorna ao procedimento de chamada.  
  
 Se o procedimento de chamada tiver um manipulador de erros ativada, ela é ativada para manipular o erro.  Se o manipulador de erro do procedimento de chamada também está ativo, o controle passa através de chamada de procedimentos anteriores até encontra um manipulador de erros ativada, mas inativo.  Se não há tal manipulador de erro for encontrado, o erro é fatal no ponto em que ele realmente ocorreu.  
  
 Cada vez que o manipulador de erro passa o controle novamente para um procedimento de chamada, esse procedimento torna\-se o procedimento atual.  Depois que um erro é manipulado por um manipulador de erro em qualquer procedimento, a execução reinicia no procedimento atual no ponto designado pelo `Resume` instrução.  
  
> [!NOTE]
>  Uma rotina de tratamento de erros não é um `Sub` procedimento ou um `Function` procedimento.  É uma seção de código marcado por um rótulo de linha ou um número de linha.  
  
## Propriedade Número  
 Rotinas de tratamento de erros se baseiam no valor da `Number` propriedade da `Err` o objeto para determinar a causa do erro.  A rotina deve testar ou salvar os valores das propriedades relevantes na `Err` antes de qualquer outro erro pode ocorrer ou antes de um procedimento que pode causar um erro é chamado de objeto.  A propriedade valores a `Err` objeto refletir apenas o erro mais recente.  A mensagem de erro associado `Err.Number` está contido no `Err.Description`.  
  
## Instrução Throw  
 Um erro que é gerado com o `Err.Raise` método define a `Exception` propriedade para uma instância recentemente criada da <xref:System.Exception> classe.  Para suportar o aumento de exceções de tipos derivados de exceção, uma `Throw` há suporte para a declaração no idioma.  Isso leva a um único parâmetro que é a instância de exceção seja lançada.  O exemplo a seguir mostra como esses recursos podem ser usados com a suporte de manipulação de exceção existente:  
  
 [!code-vb[VbVbalrErrorHandling#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_1.vb)]  
  
 Observe que o `On Error GoTo` instrução intercepta todos os erros, independentemente da classe de exceção.  
  
## On Error Resume Next  
 `On Error Resume Next`faz a execução continuar com a declaração imediatamente seguinte a instrução que causou o erro de tempo de execução, ou com a declaração imediatamente seguinte a mais recente de chamada de procedimento que contém o `On Error Resume Next` instrução.  Essa instrução permite a execução continuar, apesar de um erro de tempo de execução.  Você pode colocar a rotina de tratamento de erros onde o erro ocorreria em vez de transferência de controle para outro local dentro do procedimento.  Um `On Error Resume Next` declaração será inativa quando outro procedimento é chamado, portanto, você deve executar um `On Error Resume Next` a instrução em cada chamada rotina se desejar dentro dessa rotina de tratamento de erros de in\-line.  
  
> [!NOTE]
>  O `On Error Resume Next` construção pode ser preferível a `On Error GoTo` quando o tratamento de erros gerados durante o acesso a outros objetos.  Verificação de `Err` após cada interação com um objeto remove a ambigüidade sobre o qual o objeto foi acessado pelo código.  Pode ter certeza de qual objeto colocado o código de erro em `Err.Number`, bem como o objeto que originalmente gerou o erro \(o objeto especificado em `Err.Source`\).  
  
## On Error GoTo 0  
 `On Error GoTo 0`Desativa o tratamento de erros no procedimento atual.  Ele não especifica a linha 0 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como 0.  Sem um `On Error GoTo 0` instrução, um manipulador de erro é automaticamente desativada quando um procedimento é finalizado.  
  
## On Error GoTo \-1  
 `On Error GoTo -1`desativa a exceção do procedimento atual.  Ele não especifica a linha \-1 como o início do código de tratamento de erros, mesmo se o procedimento contenha uma linha numerada como \-1.  Sem um `On Error GoTo -1` declaração, uma exceção é automaticamente desativada quando um procedimento é finalizado.  
  
 Para impedir que o código de tratamento de erros em execução quando nenhum erro, coloque uma `Exit Sub`, `Exit Function`, ou `Exit Property` declaração imediatamente antes da rotina de tratamento de erros, como no seguinte fragmento:  
  
 [!code-vb[VbVbalrErrorHandling#18](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_2.vb)]  
  
 Aqui, o código de tratamento de erros segue a `Exit Sub` instrução e precede o `End Sub` a instrução para separar o fluxo do procedimento.  Você pode colocar o código de tratamento de erros em qualquer lugar em um procedimento.  
  
## Erros não ajustados  
 Não ajustado em objetos são retornados para o aplicativo de controle quando o objeto é executado como um arquivo executável.  Dentro do ambiente de desenvolvimento, não interceptado são retornados para o aplicativo de controle somente se as opções adequadas são definidas.  Consulte a documentação do aplicativo host para obter uma descrição dos quais opções devem ser definidas durante a depuração, como defini\-las e se o host pode criar classes.  
  
 Se você criar um objeto que acessa os outros objetos, você deve tentar tratar quaisquer erros não tratados, eles passam de volta.  Se você não pode mapear os códigos de erro em `Err.Number` a um dos seus próprios erros e passará\-los de volta para o chamador do seu objeto.  Você deve especificar o seu erro, adicionando o seu código de erro para o `VbObjectError` constante.  Por exemplo, se o código de erro está 1052, atribuí\-lo da seguinte maneira:  
  
 [!code-vb[VbVbalrErrorHandling#19](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_3.vb)]  
  
> [!CAUTION]
>  Erros do sistema durante as chamadas para bibliotecas de vínculo dinâmico \(DLLs\) do Windows não geram exceções e não podem sofrer trapping com interceptação de erros de Visual Basic.  Ao chamar funções DLL, você deve verificar cada valor de retorno de êxito ou falha \(conforme a especificações API\) e em caso de falha, verifique o valor `Err` do objeto `LastDLLError` propriedade.  
  
## Exemplo  
 Este exemplo usa primeiro o `On Error GoTo` a instrução para especificar o local de uma rotina de tratamento de erros dentro de um procedimento.  No exemplo, uma tentativa de divisão por zero gera erro número 6.  O erro é tratado na rotina de tratamento de erros e controle, em seguida, é retornado para a declaração que causou o erro.  O `On Error GoTo 0` instrução desativa a interceptação de erros.  Em seguida, a `On Error Resume Next` declaração é usada para adiar a interceptação de erros para que o contexto para o erro gerado pela próxima instrução pode ser conhecido para determinados.  Observe que `Err.Clear` é usado para limpar o `Err` propriedades do objeto após o erro é tratado.  
  
 [!code-vb[VbVbalrErrorHandling#20](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/on-error-statement_4.vb)]  
  
## Requisitos  
 **Namespace:** [VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Assembly:** Visual Basic Runtime Library \(in Microsoft.VisualBasic.dll\)  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Information.Err%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Number%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.Description%2A>   
 <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>   
 [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md)   
 [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Instrução Resume](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [Mensagens de erro](../../../visual-basic/language-reference/error-messages/index.md)   
 [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)