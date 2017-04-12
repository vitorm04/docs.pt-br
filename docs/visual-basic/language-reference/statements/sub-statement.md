---
title: Sub Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
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
ms.openlocfilehash: 0eb78f92f22502d9e8595051361b45d9bf53ed64
ms.lasthandoff: 03/13/2017

---
# <a name="sub-statement-visual-basic"></a>Instrução Sub (Visual Basic)
Declara o nome, parâmetros e código que definem um `Sub` procedimento.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>Partes  
  
-   `attributelist`  
  
     Opcional. Consulte [lista atributo](attribute-list.md).  
  
-   `Partial`  
  
     Opcional. Indica a definição de um método parcial. Consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Público](../modifiers/public.md)  
  
    -   [Protegido](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Privado](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Sobrecargas](../modifiers/overloads.md)  
  
    -   [Substituições](../modifiers/overrides.md)  
  
    -   [Substituível](../modifiers/overridable.md)  
  
    -   [NotOverridable](../modifiers/notoverridable.md)  
  
    -   [MustOverride](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     Opcional. Consulte [compartilhado](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcional. Consulte [sombras](../modifiers/shadows.md).  
  
-   `Async`  
  
     Opcional. Consulte [Async](../modifiers/async.md).  
  
-   `name`  
  
     Necessário. Nome do procedimento. Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Para criar um procedimento de construtor para uma classe, defina o nome de uma `Sub` procedimento para o `New` palavra-chave. Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Opcional. Lista de parâmetros de tipo para um procedimento genérico. Consulte [digite lista](type-list.md).  
  
-   `parameterlist`  
  
     Opcional. Lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Consulte [lista de parâmetros](parameter-list.md).  
  
-   `Implements`  
  
     Opcional. Indica que essa propriedade implementa uma ou mais `Sub` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura contendo esse procedimento. Consulte [implementa a instrução](implements-statement.md).  
  
-   `implementslist`  
  
     Necessário se `Implements` for fornecido. Lista de `Sub` procedimentos que estão sendo implementados.  
  
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
  
     Opcional. Bloco de instruções para execução deste procedimento.  
  
-   `End Sub`  
  
     Finaliza a definição desse procedimento.  
  
## <a name="remarks"></a>Comentários  
 Todos os códigos executáveis deverão estar dentro de um procedimento. Use um `Sub` quando você não desejar retornar um valor para o código de chamada de procedimento. Use uma `Function` procedimento quando desejar retornar um valor.  
  
## <a name="defining-a-sub-procedure"></a>Definindo um procedimento Sub  
 Você pode definir uma `Sub` procedimento apenas no nível de módulo. O contexto da declaração para um procedimento sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).  
  
 `Sub`padrão de procedimentos para acesso público. Você pode ajustar os níveis de acesso usando os modificadores de acesso.  
  
 Se o procedimento usa o `Implements` palavra-chave, a classe ou estrutura continente deve ter uma `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução. O `Implements` instrução deve incluir cada interface especificada no `implementslist`. No entanto, o nome pelo qual uma interface define o `Sub` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Retornando a partir de um procedimento Sub  
 Quando uma `Sub` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.  
  
 O exemplo a seguir mostra um retorno de uma `Sub` procedimento.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 O `Exit Sub` e `Return` instruções causam uma saída imediata de uma `Sub` procedimento. Qualquer número de `Exit Sub` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e `Return` instruções.  
  
## <a name="calling-a-sub-procedure"></a>Chamar um procedimento Sub  
 Chamar uma `Sub` procedimento usando o nome do procedimento em uma instrução e seguindo esse nome com sua lista de argumentos entre parênteses. Você pode omitir os parênteses somente se você não fornecer nenhum argumento. No entanto, seu código é mais legível se você sempre incluir os parênteses.  
  
 A `Sub` procedimento e uma `Function` procedimento pode ter parâmetros e executar uma série de instruções. No entanto, uma `Function` procedimento retorna um valor e um `Sub` procedimento não. Portanto, você não pode usar uma `Sub` procedimento em uma expressão.  
  
 Você pode usar o `Call` palavra-chave quando você chama um `Sub` procedimento, mas essa palavra-chave não é recomendado para a maioria dos usos. Para obter mais informações, consulte [instrução Call](call-statement.md).  
  
 Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna. Por esse motivo, se a lista de argumentos contém expressões que chamam outros procedimentos, você não deve supor que as expressões serão chamadas em uma ordem específica.  
  
## <a name="async-sub-procedures"></a>Procedimentos Sub Async  
 Usando o recurso Async, você pode chamar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.  
  
 Se você marcar um procedimento com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no procedimento. Quando o controle atinge um `Await` expressão no `Async` procedimento, o controle retorna ao chamador e progresso no procedimento está suspenso até que a tarefa aguardada seja concluída. Quando a tarefa for concluída, a execução pode retomar o procedimento.  
  
> [!NOTE]
>  Um `Async` procedimento retorna ao chamador quando ambos o primeiro objeto esperado que ainda não está completo é encontrado ou o final do `Async` procedimento for atingido, o que ocorrer primeiro.  
  
 Você também pode marcar um [instrução Function](function-statement.md) com o `Async` modificador. Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601>ou <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601> Um exemplo mais adiante neste tópico mostra um `Async` função que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601>  
  
 `Async``Sub` procedimentos são usados principalmente para manipuladores de eventos, onde um valor não pode ser retornado. Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não pode capturar exceções que o `Sub` procedimento lança.  
  
 Um `Async` procedimento não pode declarar qualquer [ByRef](../modifiers/byref.md) parâmetros.  
  
 Para obter mais informações sobre `Async` procedimentos, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [assíncronas retornam tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Sub` instrução para definir o nome, parâmetros e código que formam o corpo de uma `Sub` procedimento.  
  
 [!code-vb[VbVbalrStatements&#58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `DelayAsync` é um uma `Async``Function` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> `DelayAsync`tem um `Return` instrução que retorna um número inteiro. Portanto, a declaração de função do `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`. Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro, como mostra a seguinte instrução: `Dim result As Integer = Await delayTask`.  
  
 O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento. Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocado em espera, como mostra a seguinte instrução: `Await DoSomethingAsync()`. O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.  
  
 [!code-vb[csAsyncMethod n º&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](implements-statement.md)   
 [Instrução Function](function-statement.md)   
 [Lista de parâmetros](parameter-list.md)   
 [Instrução Dim](dim-statement.md)   
 [Instrução Call](call-statement.md)   
 [De](of-clause.md)   
 [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)   
 [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)   
 [Procedimentos de solução de problemas](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
