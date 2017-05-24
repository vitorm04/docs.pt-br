---
title: "Função Statement (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: af87477f81fab8406d726ebc8c81260b371d71c8
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="function-statement-visual-basic"></a>Instrução Function (Visual Basic)
Declara o nome, parâmetros e código que definem um `Function` procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Partes  
  
-   `attributelist`  
  
     Opcional. Consulte [lista atributo](attribute-list.md).  
  
-   `accessmodifier`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Público](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [Privado](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Sobrecargas](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [Substituições](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [Substituível](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcional. Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcional. Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
-   `Async`  
  
     Opcional. Consulte [Async](../../../visual-basic/language-reference/modifiers/async.md).  
  
-   `Iterator`  
  
     Opcional. Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).  
  
-   `name`  
  
     Necessário. Nome do procedimento. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
-   `typeparamlist`  
  
     Opcional. Lista de parâmetros de tipo para um procedimento genérico. Consulte [digite lista](type-list.md).  
  
-   `parameterlist`  
  
     Opcional. Lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Consulte [lista de parâmetros](parameter-list.md).  
  
-   `returntype`  
  
     Necessário se `Option Strict` é `On`. Tipo de dados do valor retornado por esse procedimento.  
  
-   `Implements`  
  
     Opcional. Indica que essa propriedade implementa uma ou mais `Function` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura contendo esse procedimento. Consulte [implementa a instrução](implements-statement.md).  
  
-   `implementslist`  
  
     Necessário se `Implements` for fornecido. Lista de `Function` procedimentos que estão sendo implementados.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Cada `implementedprocedure` tem a seguinte sintaxe e partes:  
  
     `interface.definedname`  
  
    |Parte|Descrição|  
    |---|---|  
    |`interface`|Necessário. Nome de uma interface implementada por esse procedimento contendo classe ou estrutura.|  
    |`definedname`|Necessário. Nome pelo qual o procedimento é definido em `interface`.|  
  
-   `Handles`  
  
     Opcional. Indica que esse procedimento pode manipular um ou mais eventos específicos. Consulte [manipula](handles-clause.md).  
  
-   `eventlist`  
  
     Necessário se `Handles` for fornecido. Lista de eventos que esse procedimento manipula.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Cada `eventspecifier` tem a seguinte sintaxe e partes:  
  
     `eventvariable.event`  
  
    |Parte|Descrição|  
    |---|---|  
    |`eventvariable`|Necessário. Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.|  
    |`event`|Necessário. Nome do evento que esse procedimento manipula.|  
  
-   `statements`  
  
     Opcional. Bloco de instruções para ser executado dentro deste procedimento.  
  
-   `End Function`  
  
     Finaliza a definição desse procedimento.  
  
## <a name="remarks"></a>Comentários  
 Todos os códigos executáveis deverão estar dentro de um procedimento. Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é conhecido como a classe, estrutura ou módulo que contém.  
  
 Para retornar um valor para o código de chamada, use uma `Function` procedimento; caso contrário, use uma `Sub` procedimento.  
  
## <a name="defining-a-function"></a>Definindo uma função  
 Você pode definir uma `Function` procedimento apenas no nível de módulo. Portanto, o contexto da declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).  
  
 `Function`padrão de procedimentos para acesso público. Você pode ajustar os níveis de acesso com os modificadores de acesso.  
  
 Um `Function` procedimento pode declarar o tipo de dados do valor que o procedimento retorna. Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface. Se você não especificar o `returntype` , o procedimento retornará `Object`.  
  
 Se esse procedimento utiliza o `Implements` palavra-chave, a classe ou estrutura continente deve também ter um `Implements` instrução que segue imediatamente o `Class` ou `Structure` instrução. O `Implements` instrução deve incluir cada interface especificada no `implementslist`. No entanto, o nome pelo qual uma interface define o `Function` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).  
  
> [!NOTE]
>  Você pode usar expressões lambda para definir a função embutida de expressões. Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="returning-from-a-function"></a>Retornar de uma função  
 Quando o `Function` procedimento retorna para o código de chamada, a execução continua com a instrução que segue a declaração que chamou o procedimento.  
  
 Para retornar um valor de uma função, você pode atribuir o valor ao nome da função ou incluí-lo em um `Return` instrução.  
  
 O `Return` instrução simultaneamente atribui o valor de retorno e sai da função, como mostra o exemplo a seguir.  
  
 [!code-vb[VbVbalrStatements&#24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa o `Exit Function` instrução para retornar.  
  
 [!code-vb[VbVbalrStatements&#23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 O `Exit Function` e `Return` instruções causam uma saída imediata de uma `Function` procedimento. Qualquer número de `Exit Function` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e `Return` instruções.  
  
 Se você usar `Exit Function` sem atribuir um valor para `name`, o procedimento retorna o valor padrão para o tipo de dados especificado em `returntype`. Se `returntype` não for especificado, o procedimento retorna `Nothing`, que é o valor padrão para `Object`.  
  
## <a name="calling-a-function"></a>Chamando uma Função  
 Chamar uma `Function` procedimento usando o nome do procedimento, seguido de lista de argumentos entre parênteses, em uma expressão. Você pode omitir os parênteses somente se você não está fornecendo quaisquer argumentos. No entanto, seu código é mais legível se você sempre incluir os parênteses.  
  
 Você chamar um `Function` procedimento da mesma maneira que você chamar qualquer biblioteca de função como `Sqrt`, `Cos`, ou `ChrW`.  
  
 Você também pode chamar uma função usando o `Call` palavra-chave. Nesse caso, o valor de retorno será ignorado. Usar o `Call` palavra-chave não é recomendado na maioria dos casos. Para obter mais informações, consulte [instrução Call](call-statement.md).  
  
 Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna. Por esse motivo, você não deve usar uma `Function` procedimento em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.  
  
## <a name="async-functions"></a>Funções assíncronas  
 O *Async* recurso permite que você chame funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.  
  
 Se você marcar uma função com o [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador na função. Quando o controle atinge um `Await` expressão no `Async` função, o controle retorna ao chamador e progresso na função está suspenso até que a tarefa aguardada seja concluída. Quando a tarefa for concluída, a execução pode retomar na função.  
  
> [!NOTE]
>  Um `Async` procedimento retorna ao chamador quando encontra o primeiro objeto esperado que não ainda foi concluído ou ou chegar ao final do `Async` procedimento, o que ocorrer primeiro.  
  
 Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601>ou <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> Um exemplo de uma `Async` função que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>é fornecido abaixo.</xref:System.Threading.Tasks.Task%601>  
  
 Um `Async` função não pode declarar qualquer [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.  
  
 A [instrução Sub](sub-statement.md) também podem ser marcados com o `Async` modificador. Isso é usado principalmente para manipuladores de eventos, onde um valor não pode ser retornado. Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não pode capturar exceções que são geradas pelo `Sub` procedimento.  
  
 Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [assíncronas retornam tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="iterator-functions"></a>Funções de iterador  
 Um *iterador* função realiza a uma iteração personalizada em uma coleção, como uma lista ou matriz. Usa uma função de iterador de [gerar](yield-statement.md) instrução para retornar cada elemento por vez. Quando um [gerar](yield-statement.md) instrução for atingida, o local atual no código será lembrado. Execução é reiniciada a partir desse local na próxima vez em que a função de iterador é chamada.  
  
 Chamar um iterador no código do cliente usando um [para cada uma... Próxima](for-each-next-statement.md) instrução.  
  
 O tipo de retorno de uma função do iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable>  
  
 Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Function` declaração para declarar o nome, parâmetros e código que formam o corpo de uma `Function` procedimento. O `ParamArray` modificador permite que a função aceite um número variável de argumentos.  
  
 [!code-vb[25 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir chama a função declarada no exemplo anterior.  
  
 [!code-vb[VbVbalrStatements&#26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `DelayAsync` é um `Async``Function` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> `DelayAsync`tem um `Return` instrução que retorna um número inteiro. Portanto, a declaração de função do `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`. Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro. Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.  
  
 O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento. Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocado em espera, como demonstra a seguinte instrução: `Await DoSomethingAsync()`. O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.  
  
 [!code-vb[csAsyncMethod n º&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução sub](sub-statement.md)   
 [Procedimentos de função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Lista de parâmetros](parameter-list.md)   
 [Instrução Dim](dim-statement.md)   
 [Instrução Call](call-statement.md)   
 [De](of-clause.md)   
 [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedimentos de solução de problemas](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Expressão de Função](../../../visual-basic/language-reference/operators/function-expression.md)

