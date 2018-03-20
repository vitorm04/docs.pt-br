---
title: "Expressões lambda (Guia de Programação em C#)"
ms.date: 03/03/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 14bb60a5009f9a1ae59ed9846ebc868cfdcc05c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="lambda-expressions-c-programming-guide"></a>Expressões lambda (Guia de Programação em C#)
Uma expressão lambda é uma [função anônima](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que você pode usar para criar [delegados](../../../csharp/programming-guide/delegates/using-delegates.md) ou tipos de [árvore de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b). Ao usar expressões lambda, você pode escrever funções locais que podem ser passadas como argumentos ou retornadas como o valor de chamadas de função. Expressões lambda são particularmente úteis para escrever expressões de consulta LINQ.  
  
 Para criar uma expressão lambda, especifique os parâmetros de entrada (se houver) no lado esquerdo do operador lambda [=>](../../../csharp/language-reference/operators/lambda-operator.md) e coloque a expressão ou o bloco de instruções do outro lado. Por exemplo, a expressão lambda `x => x * x` especifica um parâmetro chamado `x` e retorna o valor de `x` ao quadrado. Você pode atribuir essa expressão a um tipo delegado como neste exemplo:  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Para criar um tipo de árvore de expressão:  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 O operador `=>` tem a mesma precedência que a atribuição (`=`) e é [associativo direito](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (consulte a seção "Associatividade" do artigo Operadores).  
  
 Lambdas são usadas em consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] baseadas em métodos como argumentos para métodos de operador de consulta padrão como <xref:System.Linq.Enumerable.Where%2A>.  
  
 Quando você usa a sintaxe baseada em método para chamar o método <xref:System.Linq.Enumerable.Where%2A> na classe <xref:System.Linq.Enumerable> (assim como você faz em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para objetos e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) o parâmetro é um tipo delegado <xref:System.Func%602?displayProperty=nameWithType>. Uma expressão lambda é a maneira mais conveniente de criar esse delegado. Quando você chama o mesmo método, por exemplo, na classe <xref:System.Linq.Queryable?displayProperty=nameWithType> (como faz em [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), o tipo de parâmetro é uma <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\>, em que Func é qualquer delegado Func com até 16 parâmetros de entrada. Novamente, uma expressão lambda é apenas uma maneira muito concisa de construir essa árvore de expressão. Os lambdas permitem que chamadas `Where` pareçam semelhantes embora, na verdade, o tipo de objeto criado do lambda seja diferente.  
  
 No exemplo anterior, observe que a assinatura do delegado tem um parâmetro de entrada implícito inserido do tipo `int` e retorna um `int`. A expressão lambda pode ser convertida como um delegado desse tipo porque também tem um parâmetro de entrada (`x`) e um valor de retorno que o compilador pode converter implicitamente no tipo `int`. (A inferência de tipos é discutida em mais detalhes nas seções a seguir.) Quando o delegado for chamado usando um parâmetro de entrada 5, ele retornará 25 como resultado.  
  
 Lambdas não são permitidas no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md) ou [as](../../../csharp/language-reference/keywords/as.md).  
  
 Todas as restrições que se aplicam a métodos anônimos também se aplicam às expressões lambda. Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## <a name="expression-lambdas"></a>Lambdas de expressão  
 Uma expressão lambda com uma expressão no lado direito do operador => é chamada de *lambda de expressão*. Os lambdas de expressão são usados amplamente na construção de [Árvores de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b). Uma expressão lambda retorna o resultado da expressão e tem o seguinte formato básico:  
  
```csharp
(input-parameters) => expression
```

 Os parênteses serão opcionais somente se o lambda tiver um parâmetro de entrada; caso contrário, eles serão obrigatórios. Dois ou mais parâmetros de entrada são separados por vírgulas e envolvidos por parênteses:  
  
```csharp
(x, y) => x == y
```

 Às vezes, é difícil ou impossível para o compilador inferir os tipos de entrada. Quando isso ocorre, você pode especificar os tipos de maneira explícita conforme mostrado neste exemplo:  
  
```csharp
(int x, string s) => s.Length > x
```

 Especifique parâmetros de entrada zero com parênteses vazios:  
  
```csharp
() => SomeMethod()
```

 Observe no exemplo anterior que o corpo de uma expressão lambda pode consistir de uma chamada de método. No entanto, se você estiver criando árvores de expressão que serão avaliadas fora do .NET Framework, como no SQL Server, você não deverá usar chamadas de método em expressões lambda. Os métodos não terão significado fora do contexto do .NET Common Language Runtime.  
  
## <a name="statement-lambdas"></a>Lambdas de instrução  
 Um lambda de instrução lembra um lambda de expressão, exceto que as instruções estão incluídas entre chaves:  
  
(parâmetros de entrada) => { instrução; }

 O corpo de uma instrução lambda pode consistir de qualquer número de instruções; no entanto, na prática, normalmente não há mais de duas ou três.  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 Lambdas de instrução, como métodos anônimos, não podem ser usados para criar árvores de expressão.  
  
## <a name="async-lambdas"></a>Lambdas assíncronos  
 Você pode facilmente criar expressões e instruções lambda que incorporem processamento assíncrono, ao usar as palavras-chaves [async](../../../csharp/language-reference/keywords/async.md) e [await](../../../csharp/language-reference/keywords/await.md). Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 Você pode adicionar o mesmo manipulador de eventos ao usar um lambda assíncrono. Para adicionar esse manipulador, adicione um modificador `async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).  
  
## <a name="lambdas-with-the-standard-query-operators"></a>Lambdas com os operadores de consulta padrão  
 Vários operadores de consulta padrão têm um parâmetro de entrada cujo tipo é de uma família <xref:System.Func%602> de delegados genéricos. Esses delegados usam parâmetros de tipo para definir o número e os tipos de parâmetros de entrada e o tipo de retorno do delegado. delegados `Func` são muito úteis para encapsular expressões definidas pelo usuário aplicadas a cada elemento em um conjunto de dados de origem. Por exemplo, considere o seguinte tipo delegado:  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 O delegado pode ser instanciado como `Func<int,bool> myFunc` onde `int` é um parâmetro de entrada e `bool` é o valor de retorno. O valor de retorno é sempre especificado no último parâmetro de tipo. `Func<int, string, bool>` define um delegado com dois parâmetros de entrada, `int` e `string` e um tipo de retorno `bool`. O delegado `Func` a seguir, quando é chamado, retornará true ou false para indicar se o parâmetro de entrada é igual a 5:  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Você também pode fornecer uma expressão lambda quando o tipo de argumento é `Expression<Func>`, por exemplo, nos operadores de consulta padrão que são definidos em System.Linq.Queryable. Quando você especifica um argumento `Expression<Func>`, o lambda será compilado em uma árvore de expressão.  
  
 Um operador de consulta padrão, o método <xref:System.Linq.Enumerable.Count%2A>, é mostrado aqui:  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 O compilador pode inferir o tipo de parâmetro de entrada ou você também pode especificá-lo explicitamente. Essa expressão lambda em particular conta esses inteiros (`n`) que, quando dividida por dois, tem um resto 1.  
  
 A linha de código a seguir gera uma sequência que contém todos os elementos na matriz `numbers` do lado esquerdo do 9 porque esse é o primeiro número na sequência que não atende à condição:  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Este exemplo mostra como especificar vários parâmetros de entrada ao inclui-los entre parênteses. O método retorna todos os elementos na matriz de números até ser encontrado um número cujo valor seja menor do que sua posição. Não confunda o operador lambda (`=>`) com o operador greater than ou equal (`>=`).  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a>Inferência de tipos em lambdas  
 Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo lambda, no tipo delegado do parâmetro e em outros fatores conforme descrito na especificação da linguagem C#. Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem. Portanto, se você estiver consultando um `IEnumerable<Customer>`, a variável de entrada será inferida para ser um objeto `Customer`, o que significa que você tem acesso aos seus métodos e propriedades:  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 As regras gerais para lambdas são:  
  
-   O lambda deve conter o mesmo número de parâmetros do tipo delegado.  
  
-   Cada parâmetro de entrada no lambda deve ser implicitamente conversível em seu parâmetro delegado correspondente.  
  
-   O valor de retorno do lambda (se houver) deve ser implicitamente conversível para o tipo de retorno do delegado.  
  
 Observe que as expressões lambda em si não têm um tipo porque o sistema de tipo comum não possui conceito intrínseco da "expressão lambda". No entanto, às vezes é conveniente falar informalmente do "tipo" de uma expressão lambda. Nesses casos, o tipo se refere ao tipo delegado ou tipo <xref:System.Linq.Expressions.Expression> ao qual a expressão lambda é convertida.  
  
## <a name="variable-scope-in-lambda-expressions"></a>Escopo variável em expressões lambda  
 As lambdas podem se referir a *variáveis externas* (consulte [Métodos Anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) que estão no escopo do método que define a função lambda ou no escopo do tipo que contém a expressão lambda. As variáveis que são capturadas dessa forma são armazenadas para uso na expressão lambda mesmo que de alguma outra forma elas saíssem do escopo e fossem coletadas como lixo. Uma variável externa deve ser definitivamente atribuída para que possa ser consumida em uma expressão lambda. O exemplo a seguir demonstra estas regras:  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 As seguintes regras se aplicam ao escopo variável em expressões lambda:  
  
-   Uma variável capturada não será coletada do lixo até que o delegado que faz referência a ela se qualifique para coleta de lixo.  
  
-   As variáveis introduzidas em uma expressão lambda não são visíveis no método externo.  
  
-   Uma expressão lambda não pode capturar um parâmetro `in`, `ref` ou `out` diretamente de um método delimitador.  
  
-   Uma instrução return em uma expressão lambda não faz com que o método delimitador retorne.  
  
-   Uma expressão lambda não poderá conter uma instrução `goto`, `break` ou `continue` que está dentro da função lambda se o destino da instrução jump estiver fora do bloco. Também será um erro ter uma instrução jump fora do bloco da função lambda se o destino estiver dentro do bloco.  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a>Capítulo do Livro em Destaque  
 [Expressões lambda, eventos e delegados](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [LINQ (Consulta Integrada à Linguagem)](../../../csharp/programming-guide/concepts/linq/index.md)  
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [Árvores de Expressão](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Exemplos de C# do Visual Studio 2008 (veja os arquivos de exemplo de consultas LINQ e programa XQuery)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [Expressões lambda recursivas](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
