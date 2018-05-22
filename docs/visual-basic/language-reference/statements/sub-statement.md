---
title: Instrução Sub (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 08be38cdbec82914b567ab5b86eed71181efcf57
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
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
  
     Opcional. Consulte [lista de atributos](attribute-list.md).  
  
-   `Partial`  
  
     Opcional. Indica a definição de um método parcial. Consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Opcional. Pode ser um dos seguintes:  
  
    -   [Público](../modifiers/public.md)  
  
    -   [Protegido](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Privado](../modifiers/private.md)  
  
    - [Friend protegido](../../language-reference/modifiers/protected-friend.md)

    - [Privado protegido](../../language-reference/modifiers/private-protected.md)
  
     Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
-   `proceduremodifiers`  
  
     Opcional. Pode ser um dos seguintes:  
  
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
  
     Necessário. Nome do procedimento. Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave. Para obter mais informações, consulte [vida útil do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Opcional. Lista de parâmetros de tipo para um procedimento genérico. Consulte [digite lista](type-list.md).  
  
-   `parameterlist`  
  
     Opcional. Lista de nomes de variáveis locais que representa os parâmetros deste procedimento. Consulte [lista de parâmetros](parameter-list.md).  
  
-   `Implements`  
  
     Opcional. Indica que esse procedimento implementa uma ou mais `Sub` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém esse procedimento. Consulte [implementa a instrução](implements-statement.md).  
  
-   `implementslist`  
  
     Necessário se `Implements` for fornecido. Lista de `Sub` procedimentos sendo implementados.  
  
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
  
     Necessário se `Handles` for fornecido. Lista de eventos que trata este procedimento.  
  
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
 Todo o código executável deve estar dentro de um procedimento. Use um `Sub` quando você não quiser retornar um valor para o código de chamada de procedimento. Use um `Function` procedimento quando você quiser retornar um valor.  
  
## <a name="defining-a-sub-procedure"></a>Definindo um procedimento Sub  
 Você pode definir um `Sub` procedimento apenas no nível de módulo. O contexto da declaração para um procedimento sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).  
  
 `Sub` padrão de procedimentos para acesso público. Você pode ajustar os níveis de acesso usando os modificadores de acesso.  
  
 Se o procedimento usa o `Implements` deve ter a palavra-chave, a classe ou estrutura contendo um `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução. O `Implements` instrução deve incluir cada interface que é especificado em `implementslist`. No entanto, o nome pelo qual uma interface define o `Sub` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Retornando a partir de um procedimento Sub  
 Quando uma `Sub` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.  
  
 O exemplo a seguir mostra um retorno de uma `Sub` procedimento.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 O `Exit Sub` e `Return` instruções produzem saída imediata de um `Sub` procedimento. Qualquer número de `Exit Sub` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e `Return` instruções.  
  
## <a name="calling-a-sub-procedure"></a>Chamar um procedimento Sub  
 Você chama um `Sub` procedimento usando o nome do procedimento em uma instrução e, em seguida, seguir esse nome com a lista de argumentos entre parênteses. Você pode omitir os parênteses somente se você não fornecer nenhum argumento. No entanto, seu código é mais legível se você sempre incluir os parênteses.  
  
 Um `Sub` procedimento e um `Function` procedimento pode ter parâmetros e executar uma série de instruções. No entanto, um `Function` procedimento retorna um valor e um `Sub` procedimento não. Portanto, você não pode usar um `Sub` procedimento em uma expressão.  
  
 Você pode usar o `Call` palavra-chave quando você chama um `Sub` procedimento, mas essa palavra-chave não é recomendado para a maioria dos usos. Para obter mais informações, consulte [instrução Call](call-statement.md).  
  
 Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna. Por esse motivo, se a lista de argumento inclui expressões que chamam outros procedimentos, você não deve presumir que as expressões serão chamadas em uma ordem específica.  
  
## <a name="async-sub-procedures"></a>Procedimentos Sub Async  
 Usando o recurso de assíncrona, você pode chamar funções assíncronas sem o uso de retornos de chamada explícitos ou dividir manualmente seu código pelas várias funções ou expressões lambda.  
  
 Se você marcar um procedimento com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no procedimento. Controlar quando chega uma `Await` expressão no `Async` procedimento, o controle retorna ao chamador e o andamento do procedimento fica suspenso até que a tarefa em espera é concluída. Quando a tarefa for concluída, pode retomar a execução do procedimento.  
  
> [!NOTE]
>  Um `Async` procedimento retorna ao chamador quando é encontrado ou o primeiro objeto em espera que ainda não foi concluído ou até o fim do `Async` procedimento for atingido, o que ocorrer primeiro.  
  
 Você também pode marcar um [instrução Function](function-statement.md) com o `Async` modificador. Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Um exemplo mais tarde neste tópico mostra um `Async` função que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>.  
  
 `Async` `Sub` os procedimentos são usados principalmente para manipuladores de eventos, onde um valor não pode ser retornado. Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não é possível capturar exceções que o `Sub` procedimento lança.  
  
 Um `Async` procedimento não pode declarar qualquer [ByRef](../modifiers/byref.md) parâmetros.  
  
 Para obter mais informações sobre `Async` procedimentos, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [Async retornar tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Sub` instrução para definir o nome, parâmetros e código que formam o corpo de uma `Sub` procedimento.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, `DelayAsync` é um `Async``Function` que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>. `DelayAsync` tem uma instrução `Return` que retorna um número inteiro. Portanto, a declaração da função de `DelayAsync` deve ter um tipo de retorno `Task(Of Integer)`. Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro, como mostra a instrução a seguir: `Dim result As Integer = Await delayTask`.  
  
 O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento. Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada `DoSomethingAsync` deve ser aguardada, como mostra a instrução a seguir: `Await DoSomethingAsync()`. O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Implements](implements-statement.md)  
 [Instrução Function](function-statement.md)  
 [Lista de Parâmetros](parameter-list.md)  
 [Instrução Dim](dim-statement.md)  
 [Instrução Call](call-statement.md)  
 [Of](of-clause.md)  
 [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [Como usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
