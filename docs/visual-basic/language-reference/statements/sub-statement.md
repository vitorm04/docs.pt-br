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
ms.openlocfilehash: e7015474a0617b76ca537d2e84e8d7bfc72b6e12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737657"
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
  
     Opcional. Ver [lista de atributos](attribute-list.md).  
  
-   `Partial`  
  
     Opcional. Indica a definição de um método parcial. Ver [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).  
  
-   `accessmodifier`  
  
     Opcional. Pode ser uma das seguintes opções:  
  
    -   [Público](../modifiers/public.md)  
  
    -   [Protegido](../modifiers/protected.md)  
  
    -   [Friend](../modifiers/friend.md)  
  
    -   [Privado](../modifiers/private.md)  
  
    - [Amigo Protegido](../../language-reference/modifiers/protected-friend.md)

    - [Particular Protegido](../../language-reference/modifiers/private-protected.md)
  
     Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
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
  
     Opcional. Ver [compartilhado](../modifiers/shared.md).  
  
-   `Shadows`  
  
     Opcional. Ver [sombras](../modifiers/shadows.md).  
  
-   `Async`  
  
     Opcional. Ver [Async](../modifiers/async.md).  
  
-   `name`  
  
     Necessário. Nome do procedimento. Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md). Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave. Para obter mais informações, consulte [tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).  
  
-   `typeparamlist`  
  
     Opcional. Lista de parâmetros de tipo para um procedimento genérico. Ver [lista de tipos](type-list.md).  
  
-   `parameterlist`  
  
     Opcional. Lista de nomes de variáveis locais que representam os parâmetros deste procedimento. Ver [lista de parâmetros](parameter-list.md).  
  
-   `Implements`  
  
     Opcional. Indica que esse procedimento implementa uma ou mais `Sub` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém esse procedimento. Ver [implementa a instrução](implements-statement.md).  
  
-   `implementslist`  
  
     Necessário se `Implements` for fornecido. Lista de `Sub` procedimentos que está sendo implementados.  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     Cada `implementedprocedure` tem a seguinte sintaxe e partes:  
  
     `interface.definedname`  
  
    |Parte|Descrição|  
    |---|---|  
    |`interface`|Necessário. Que contém o nome de uma interface implementada por esse procedimento classe ou estrutura.|  
    |`definedname`|Necessário. Nome pelo qual o procedimento é definido em `interface`.|  
  
-   `Handles`  
  
     Opcional. Indica que esse procedimento pode manipular um ou mais eventos específicos. Ver [manipula](handles-clause.md).  
  
-   `eventlist`  
  
     Necessário se `Handles` for fornecido. Lista de eventos que manipula esse procedimento.  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     Cada `eventspecifier` tem a seguinte sintaxe e partes:  
  
     `eventvariable.event`  
  
    |Parte|Descrição|  
    |---|---|  
    |`eventvariable`|Necessário. Variável de objeto declarado com o tipo de dados da classe ou estrutura que gera o evento.|  
    |`event`|Necessário. Nome do evento que lida com esse procedimento.|  
  
-   `statements`  
  
     Opcional. Bloco de instruções para executar dentro deste procedimento.  
  
-   `End Sub`  
  
     Finaliza a definição desse procedimento.  
  
## <a name="remarks"></a>Comentários  
 Todo o código executável deve ser dentro de um procedimento. Use um `Sub` quando você não quiser retornar um valor para o código de chamada de procedimento. Use um `Function` procedimento quando desejar retornar um valor.  
  
## <a name="defining-a-sub-procedure"></a>Definindo um procedimento Sub  
 Você pode definir um `Sub` procedimento apenas no nível de módulo. O contexto da declaração para um procedimento sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco. Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).  
  
 `Sub` padrão de procedimentos para acesso público. Você pode ajustar os níveis de acesso usando os modificadores de acesso.  
  
 Se o procedimento usa o `Implements` deve ter a palavra-chave, a classe ou estrutura contendo um `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução. O `Implements` instrução deve incluir cada interface que é especificado no `implementslist`. No entanto, o nome pelo qual uma interface define os `Sub` (no `definedname`) não precisa corresponder ao nome do procedimento (no `name`).  
  
## <a name="returning-from-a-sub-procedure"></a>Retornando de um procedimento Sub  
 Quando um `Sub` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.  
  
 O exemplo a seguir mostra um retorno de um `Sub` procedimento.  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 O `Exit Sub` e `Return` instruções fazem com que uma saída imediata de uma `Sub` procedimento. Qualquer número de `Exit Sub` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e `Return` instruções.  
  
## <a name="calling-a-sub-procedure"></a>Chamar um procedimento Sub  
 Você chama um `Sub` procedimento usando o nome do procedimento em uma instrução e, em seguida, seguindo esse nome com sua lista de argumentos entre parênteses. Você pode omitir os parênteses somente se você não fornecer nenhum argumento. No entanto, seu código é mais legível, se você sempre incluir os parênteses.  
  
 Um `Sub` procedimento e um `Function` procedimento pode ter parâmetros e executar uma série de instruções. No entanto, uma `Function` procedimento retorna um valor e um `Sub` não de procedimento. Portanto, é possível usar um `Sub` procedimento em uma expressão.  
  
 Você pode usar o `Call` palavra-chave quando você chama um `Sub` procedimento, mas essa palavra-chave não é recomendado para a maioria dos usos. Para obter mais informações, consulte [instrução Call](call-statement.md).  
  
 Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna. Por esse motivo, se a lista de argumento inclui expressões que chamam outros procedimentos, você não deve presumir que as expressões serão chamadas em uma ordem específica.  
  
## <a name="async-sub-procedures"></a>Procedimentos Sub Async  
 Ao usar o recurso Async, você pode chamar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.  
  
 Se você marcar um procedimento com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no procedimento. Quando o controle atinge uma `Await` expressão no `Async` procedimento, o controle retorna ao chamador e o progresso no procedimento é suspenso até que a tarefa aguardada seja concluída. Quando a tarefa for concluída, a execução pode retomar no procedimento.  
  
> [!NOTE]
>  Uma `Async` procedimento retorna ao chamador quando ambos o primeiro objeto esperado que ainda não está completo é encontrado ou o final do `Async` procedimento for atingido, o que ocorrer primeiro.  
  
 Você também pode marcar um [instrução Function](function-statement.md) com o `Async` modificador. Uma `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>. Um exemplo mais adiante neste tópico mostra uma `Async` que tem um tipo de retorno da função <xref:System.Threading.Tasks.Task%601>.  
  
 `Async` `Sub` procedimentos são usados principalmente para manipuladores de eventos, onde um valor não pode ser retornado. Uma `Async` `Sub` procedimento não pode ser esperado e o chamador de um `Async` `Sub` procedimento não pode capturar exceções que o `Sub` procedimento gera.  
  
 Uma `Async` procedimento não pode declarar qualquer [ByRef](../modifiers/byref.md) parâmetros.  
  
 Para obter mais informações sobre `Async` procedimentos, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `Sub` instrução para definir o nome, parâmetros e código que formam o corpo de uma `Sub` procedimento.  
  
 [!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir `DelayAsync` é um `Async` `Function` que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>. `DelayAsync` tem uma instrução `Return` que retorna um número inteiro. Portanto, a declaração da função de `DelayAsync` deve ter um tipo de retorno `Task(Of Integer)`. Porque é o tipo de retorno `Task(Of Integer)`, a avaliação do `Await` expressão na `DoSomethingAsync` produz um inteiro, como mostra a seguinte instrução: `Dim result As Integer = Await delayTask`.  
  
 O `startButton_Click` procedimento é um exemplo de um `Async Sub` procedimento. Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocada em espera, como mostra a seguinte instrução: `Await DoSomethingAsync()`. O `startButton_Click` `Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]  
  
## <a name="see-also"></a>Consulte também
- [Instrução Implements](implements-statement.md)
- [Instrução Function](function-statement.md)
- [Lista de Parâmetros](parameter-list.md)
- [Instrução Dim](dim-statement.md)
- [Instrução Call](call-statement.md)
- [Of](of-clause.md)
- [Matrizes de Parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Solução de problemas de Procedimentos](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
