---
title: Instrução On Error
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
ms.openlocfilehash: d62c2ba1849b7015ed877d503220026a2dfeff57
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353813"
---
# <a name="on-error-statement-visual-basic"></a>Instrução On Error (Visual Basic)
Habilita uma rotina de tratamento de erros e especifica o local da rotina dentro de um procedimento; também pode ser usado para desabilitar uma rotina de tratamento de erros. A instrução `On Error` é usada no tratamento de erros não estruturado e pode ser usada em vez de manipulação de exceção estruturada. A [manipulação de exceção estruturada](../../../standard/exceptions/index.md) é criada no .net, geralmente é mais eficiente e, portanto, é recomendada ao lidar com erros de tempo de execução em seu aplicativo.

 Sem tratamento de erro ou tratamento de exceção, qualquer erro de tempo de execução que ocorra é fatal: uma mensagem de erro é exibida e a execução é interrompida.

> [!NOTE]
> A palavra-chave `Error` também é usada na [instrução Error](../../../visual-basic/language-reference/statements/error-statement.md), que tem suporte para compatibilidade com versões anteriores.

## <a name="syntax"></a>Sintaxe

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>Partes

|Termo|Definição|
|---|---|
|*linha* de `GoTo`|Habilita a rotina de tratamento de erros que começa na linha especificada no argumento de *linha* necessário. O argumento de *linha* é qualquer rótulo de linha ou número de linha. Se ocorrer um erro em tempo de execução, controle as ramificações para a linha especificada, tornando o manipulador de erros ativo. A linha especificada deve estar no mesmo procedimento que a instrução `On Error` ou ocorrerá um erro de tempo de compilação.|
|`GoTo 0`|Desabilita o manipulador de erro habilitado no procedimento atual e o redefine como `Nothing`.|
|`GoTo -1`|Desabilita a exceção habilitada no procedimento atual e a redefine como `Nothing`.|
|`Resume Next`|Especifica que quando ocorrer um erro em tempo de execução, o controle vai para a instrução imediatamente após a instrução em que ocorreu o erro e a execução continua desse ponto. Use esse formulário em vez de `On Error GoTo` ao acessar objetos.|

## <a name="remarks"></a>Comentários

> [!NOTE]
> É recomendável que você use manipulação de exceção estruturada em seu código sempre que possível, em vez de usar a manipulação de exceção não estruturada e a instrução de `On Error`. Para obter mais informações, consulte [Instrução Try...Catch...Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

 Um manipulador de erro "habilitado" é um que é ativado por uma instrução `On Error`. Um manipulador de erro "ativo" é um manipulador habilitado que está no processo de tratamento de um erro.

 Se ocorrer um erro enquanto um manipulador de erro estiver ativo (entre a ocorrência do erro e uma `Resume`, `Exit Sub`, `Exit Function`ou instrução `Exit Property`), o manipulador de erros do procedimento atual não poderá tratar o erro. O controle retorna para o procedimento de chamada.
  
 Se o procedimento de chamada tiver um manipulador de erro habilitado, ele será ativado para manipular o erro. Se o manipulador de erro do procedimento de chamada também estiver ativo, o controle passa de volta pelos procedimentos de chamada anteriores até que um manipulador de erro habilitado, mas inativo, seja encontrado. Se nenhum manipulador de erro desse tipo for encontrado, o erro será fatal no ponto em que ele realmente ocorreu.
  
 Cada vez que o manipulador de erro passa o controle de volta para um procedimento de chamada, esse procedimento torna-se o procedimento atual. Depois que um erro é manipulado por um manipulador de erro em qualquer procedimento, a execução é retomada no procedimento atual no ponto designado pela instrução `Resume`.
  
> [!NOTE]
> Uma rotina de tratamento de erros não é um procedimento `Sub` ou um procedimento `Function`. É uma seção de código marcada por um rótulo de linha ou um número de linha.
  
## <a name="number-property"></a>Propriedade Number
 As rotinas de tratamento de erros dependem do valor na propriedade `Number` do objeto `Err` para determinar a causa do erro. A rotina deve testar ou salvar valores de propriedade relevantes no objeto `Err` antes que qualquer outro erro possa ocorrer ou antes que um procedimento que possa causar um erro seja chamado. Os valores de propriedade no objeto `Err` refletem apenas o erro mais recente. A mensagem de erro associada a `Err.Number` está contida em `Err.Description`.  
  
## <a name="throw-statement"></a>Instrução Throw  
 Um erro que é gerado com o método `Err.Raise` define a propriedade `Exception` como uma instância recém-criada da classe <xref:System.Exception>. Para oferecer suporte à geração de exceções de tipos de exceção derivadas, há suporte para uma instrução `Throw` no idioma. Isso usa um único parâmetro que é a instância de exceção a ser gerada. O exemplo a seguir mostra como esses recursos podem ser usados com o suporte para manipulação de exceção existente:

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 Observe que a instrução `On Error GoTo` intercepta todos os erros, independentemente da classe de exceção.
  
## <a name="on-error-resume-next"></a>Se houver erro, retome avançar
 `On Error Resume Next` faz com que a execução continue com a instrução imediatamente após a instrução que causou o erro de tempo de execução, ou com a instrução imediatamente após a chamada mais recente do procedimento que contém a instrução `On Error Resume Next`. Essa instrução permite que a execução continue apesar de um erro de tempo de execução. Você pode colocar a rotina de tratamento de erros em que o erro ocorreria em vez de transferir o controle para outro local dentro do procedimento. Uma instrução `On Error Resume Next` se torna inativa quando outro procedimento é chamado, portanto, você deve executar uma instrução `On Error Resume Next` em cada rotina chamada se desejar o tratamento de erros embutidos dentro dessa rotina.
  
> [!NOTE]
> A construção de `On Error Resume Next` pode ser preferível a `On Error GoTo` ao manipular erros gerados durante o acesso a outros objetos. A verificação de `Err` após cada interação com um objeto remove a ambiguidade sobre qual objeto foi acessado pelo código. Você pode ter certeza de qual objeto colocou o código de erro em `Err.Number`, bem como qual objeto gerou originalmente o erro (o objeto especificado em `Err.Source`).

## <a name="on-error-goto-0"></a>Se houver erro, GoTo 0
 `On Error GoTo 0` desabilita o tratamento de erros no procedimento atual. Ele não especifica a linha 0 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada como 0. Sem uma instrução `On Error GoTo 0`, um manipulador de erro é desabilitado automaticamente quando um procedimento é encerrado.

## <a name="on-error-goto--1"></a>Se houver erro GoTo-1
 `On Error GoTo -1` desabilita a exceção no procedimento atual. Ele não especifica a linha 1 como o início do código de tratamento de erros, mesmo que o procedimento contenha uma linha numerada-1. Sem uma instrução `On Error GoTo -1`, uma exceção é desabilitada automaticamente quando um procedimento é encerrado.

 Para evitar que o código de tratamento de erros seja executado quando não houve erro, coloque uma instrução `Exit Sub`, `Exit Function`ou `Exit Property` imediatamente antes da rotina de tratamento de erros, como no fragmento a seguir:

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 Aqui, o código de tratamento de erros segue a instrução `Exit Sub` e precede a instrução `End Sub` para separá-la do fluxo de procedimento. Você pode posicionar o código de tratamento de erros em qualquer lugar em um procedimento.

## <a name="untrapped-errors"></a>Erros não interceptados
 Erros não interceptados em objetos são retornados ao aplicativo de controle quando o objeto está sendo executado como um arquivo executável. No ambiente de desenvolvimento, os erros não interceptados serão retornados para o aplicativo de controle somente se as opções apropriadas estiverem definidas. Consulte a documentação do aplicativo host para obter uma descrição de quais opções devem ser definidas durante a depuração, como defini-las e se o host pode criar classes.

 Se você criar um objeto que acessa outros objetos, deverá tentar lidar com os erros não manipulados que eles passam de volta. Se você não puder, mapeie os códigos de erro em `Err.Number` para um de seus próprios erros e, em seguida, passe-os de volta para o chamador do seu objeto. Você deve especificar seu erro adicionando o código de erro à constante `VbObjectError`. Por exemplo, se o código de erro for 1052, atribua-o da seguinte maneira:

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Os erros do sistema durante chamadas para DLLs (bibliotecas de vínculo dinâmico) do Windows não geram exceções e não podem ser interceptados com Visual Basic interceptação de erro. Ao chamar as funções de DLL, você deve verificar cada valor de retorno para êxito ou falha (de acordo com as especificações de API) e, em caso de falha, verifique o valor na propriedade `LastDLLError` do objeto de `Err`.

## <a name="example"></a>Exemplo
 Este exemplo primeiro usa a instrução `On Error GoTo` para especificar o local de uma rotina de tratamento de erros dentro de um procedimento. No exemplo, uma tentativa de dividir por zero gera o erro número 6. O erro é tratado na rotina de tratamento de erros e, em seguida, o controle é retornado para a instrução que causou o erro. A instrução `On Error GoTo 0` desativa a interceptação de erros. Em seguida, a instrução `On Error Resume Next` é usada para adiar a interceptação de erros para que o contexto do erro gerado pela próxima instrução possa ser conhecido para determinados. Observe que `Err.Clear` é usado para limpar as propriedades do objeto `Err` depois que o erro é manipulado.

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}
 **Namespace:** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)

 **Assembly:** Visual Basic a biblioteca de tempo de execução (em Microsoft. VisualBasic. dll)

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
