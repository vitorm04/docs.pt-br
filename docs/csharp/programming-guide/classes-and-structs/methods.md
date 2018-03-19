---
title: "Métodos (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5390ee08ddd0f4725bb42bbdf7240bb99bd25301
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="methods-c-programming-guide"></a>Métodos (Guia de Programação em C#)
Um método é um bloco de código que contém uma série de instruções. Um programa faz com que as instruções sejam executadas chamando o método e especificando os argumentos de método necessários. No C#, todas as instruções executadas são realizadas no contexto de um método. O método Main é o ponto de entrada para todos os aplicativos C# e é chamado pelo CLR (Common Language Runtime) quando o programa é iniciado.  
  
> [!NOTE]
>  Este tópico aborda os métodos nomeados. Para obter informações sobre funções anônimas, consulte [Funções anônimas](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Assinaturas de Método  
 Os métodos são declarados em uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) especificando o nível de acesso, como `public` ou `private`, modificadores opcionais, como `abstract` ou `sealed`, o valor retornado, o nome do método e os parâmetros de método. Juntas, essas partes são a assinatura do método.  
  
> [!NOTE]
>  Um tipo de retorno de um método não faz parte da assinatura do método para fins de sobrecarga de método. No entanto, ele faz parte da assinatura do método ao determinar a compatibilidade entre um delegado e o método para o qual ele aponta.  
  
 Os parâmetros de método estão entre parênteses e separados por vírgulas. Parênteses vazios indicam que o método não requer parâmetros. Essa classe contém três métodos:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Acesso a método  
 Chamar um método em um objeto é como acessar um campo. Após o nome do objeto, adicione um ponto final, o nome do método e parênteses. Os argumentos são listados dentro dos parênteses e são separados por vírgulas. Os métodos da classe `Motorcycle` podem, portanto, ser chamados como no exemplo a seguir:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Parâmetros de método versus Arguments  
 A definição do método especifica os nomes e tipos de quaisquer parâmetros obrigatórios. Quando o código de chamada chama o método, ele fornece valores concretos, chamados argumentos, para cada parâmetro. Os argumentos devem ser compatíveis com o tipo de parâmetro, mas o nome do argumento (se houver) usado no código de chamada não precisa ser o mesmo que o parâmetro nomeado definido no método. Por exemplo:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Passagem por referência versus passagem por valor  
 Por padrão, quando um tipo de valor é passado para um método, uma cópia é passada em vez do objeto propriamente dito. Portanto, alterações no argumento não têm nenhum efeito sobre a cópia original no método de chamada. Você pode passar um tipo de valor por referência usando a palavra-chave ref. Para obter mais informações, consulte [Passando parâmetros de tipo de valor](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Para obter uma lista de tipos de valor internos, consulte [Tabela de tipos de valor](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Quando um objeto de tipo de referência é passado para um método, uma referência ao objeto é passada. Ou seja, o método recebe não o objeto em si, mas um argumento que indica o local do objeto. Se você alterar um membro do objeto usando essa referência, a alteração será refletida no argumento no método de chamada, ainda que você passe o objeto por valor.  
  
 Crie um tipo de referência usando a palavra-chave `class`, como mostra o exemplo a seguir.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Agora, se você passar um objeto com base nesse tipo para um método, uma referência ao objeto será passada. O exemplo a seguir passa um objeto do tipo `SampleRefType` ao método `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 O exemplo faz essencialmente a mesma coisa que o exemplo anterior, pois ele passa um argumento por valor para um método. No entanto, como um tipo de referência é usado, o resultado é diferente. A modificação feita em `ModifyObject` para o campo `value` do parâmetro, `obj`, também altera o campo `value` do argumento, `rt`, no método `TestRefType`. O método `TestRefType` exibe 33 como a saída.  
  
 Para obter mais informações sobre como passar tipos de referência por referência e por valor, consulte [Passando parâmetros de tipo de referência](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) e [Tipos de referência](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Valores de Retorno  
Os métodos podem retornar um valor para o chamador. Se o tipo de retorno, o tipo listado antes do nome do método, não for `void`, o método poderá retornar o valor usando a palavra-chave `return`. Uma instrução com a palavra-chave `return` seguida por uma variável que corresponde ao tipo de retorno retornará esse valor ao chamador do método. 

O valor pode ser retornado ao chamador por valor ou, do C# 7 em diante, [por referência](ref-returns.md). Valores são retornados ao chamador por referência se a `ref` palavra-chave é usada na assinatura do método e segue cada palavra-chave `return`. Por exemplo, a instrução de retorno e a assinatura de método a seguir indicam que o método retorna uma variável chamada `estDistance` por referência para o chamador.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

A palavra-chave `return` também interrompe a execução do método. Se o tipo de retorno for `void`, uma instrução `return` sem um valor ainda será útil para interromper a execução do método. Sem a palavra-chave `return`, a execução do método será interrompida quando chegar ao final do bloco de código. Métodos com um tipo de retorno não nulo devem usar a palavra-chave `return` para retornar um valor. Por exemplo, esses dois métodos usam a palavra-chave `return` para retornar inteiros:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Para usar um valor retornado de um método, o método de chamada pode usar a chamada de método em si em qualquer lugar que um valor do mesmo tipo seria suficiente. Você também pode atribuir o valor retornado a uma variável. Por exemplo, os dois exemplos de código a seguir obtêm a mesma meta:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Usar uma variável local, nesse caso, `result`, para armazenar um valor é opcional. Isso pode ajudar a legibilidade do código ou pode ser necessário se você precisar armazenar o valor original do argumento para todo o escopo do método.  

Para usar o valor retornado de um método por referência, você deve declarar uma variável [ref local](ref-returns.md#ref-locals) se você pretende modificar seu valor. Por exemplo, se o método `Planet.GetEstimatedDistance` retorna um valor <xref:System.Double> por referência, você pode defini-lo como uma variável ref local com código semelhante ao seguinte:

```csharp
ref int distance = plant 
```

Retornar uma matriz multidimensional de um método, `M`, que modifica o conteúdo da matriz, não é necessário se a função de chamada passou a matriz para `M`.  Você pode retornar a matriz resultante de `M` para um bom estilo ou fluxo funcional de valores, mas isso não é necessário porque o C# passa todos os tipos de referência por valor e o valor de uma referência de matriz é o ponteiro para a matriz. No método `M`, as alterações do conteúdo da matriz podem ser observadas por qualquer código que tiver uma referência à matriz, conforme mostrado no exemplo a seguir.  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 Para obter mais informações, consulte [return](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Métodos assíncronos  
 Usando o recurso async, você pode invocar métodos assíncronos sem usar retornos de chamada explícitos ou dividir manualmente seu código entre vários métodos ou expressões lambda. 
  
 Se marcar um método com o modificador [async](../../../csharp/language-reference/keywords/async.md), você poderá usar o operador [await](../../../csharp/language-reference/keywords/await.md) no método. Quando o controle atinge uma expressão await no método assíncrono, ele retorna para o chamador e o progresso no método é suspenso até a tarefa aguardada ser concluída. Quando a tarefa for concluída, a execução poderá ser retomada no método.  
  
> [!NOTE]
>  Um método assíncrono retorna para o chamador quando encontra o primeiro objeto esperado que ainda não está completo ou chega ao final do método assíncrono, o que ocorrer primeiro.  
  
 Um método assíncrono pode conter um tipo de retorno <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> ou nulo. O tipo de retorno nulo é usado principalmente para definir manipuladores de eventos, em que um tipo de retorno nulo é necessário. Um método assíncrono que retorna nulo não pode ser aguardado e o chamador de um método de retorno nulo não pode capturar as exceções que esse método gera.  
  
 No exemplo a seguir, `DelayAsync` é um método assíncrono que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>. `DelayAsync` tem uma instrução `return` que retorna um número inteiro. Portanto, a declaração do método de `Task<int>` deve ter um tipo de retorno de `DelayAsync`. Como o tipo de retorno é `Task<int>`, a avaliação da expressão `await` em `DoSomethingAsync` produz um inteiro, como a instrução a seguir demonstra: `int result = await delayTask`.  
  
 O método `startButton_Click` é um exemplo de método assíncrono que tem um tipo de retorno nulo. Como `DoSomethingAsync` é um método assíncrono, a tarefa para a chamada para `DoSomethingAsync` deve ser colocada em espera, como mostra a seguinte instrução: `await DoSomethingAsync();`. O método `startButton_Click` deve ser definido com o modificador `async` porque o método tem uma expressão `await`.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Um método assíncrono não pode declarar nenhum parâmetro [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), mas pode chamar métodos com tais parâmetros.  
  
 Para obter mais informações sobre os métodos assíncronos, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md), [Fluxo de controle em programas assíncronos](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md) e [Tipos de retorno assíncronos](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Definições de corpo de expressão  
 É comum ter definições de método que simplesmente retornam imediatamente com o resultado de uma expressão ou que têm uma única instrução como o corpo do método.  Há um atalho de sintaxe para definir esses métodos usando `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Se o método retornar `void` ou for um método assíncrono, o corpo do método deverá ser uma expressão de instrução (igual às lambdas).  Para propriedades e indexadores, eles devem ser somente leitura e você não usa a palavra-chave do acessador `get`.  
  
## <a name="iterators"></a>Iterators  
 Um iterador realiza uma iteração personalizada em uma coleção, como uma lista ou uma matriz. Um iterador usa a instrução [yield return](../../../csharp/language-reference/keywords/yield.md) para retornar um elemento de cada vez. Quando uma instrução [yield return](../../../csharp/language-reference/keywords/yield.md) for alcançada, o local atual no código será lembrado. A execução será reiniciada desse local quando o iterador for chamado na próxima vez.  
  
 Você chama um iterador de um código de cliente usando uma instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  
  
 O tipo de retorno de um iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Classes e Structs](index.md)  
 [Modificadores de acesso](access-modifiers.md)  
 [Classes static e membros de classes static](static-classes-and-static-class-members.md)  
 [Herança](inheritance.md)  
 [Classes e membros de classes abstract e sealed](abstract-and-sealed-classes-and-class-members.md)  
 [params](../../../csharp/language-reference/keywords/params.md)  
 [return](../../../csharp/language-reference/keywords/return.md)  
 [out](../../../csharp/language-reference/keywords/out.md)  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [Passando parâmetros](passing-parameters.md)
