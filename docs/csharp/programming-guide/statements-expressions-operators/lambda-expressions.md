---
title: Expressões lambda (Guia de Programação em C#)
ms.date: 03/03/2017
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: f20ba6845a6a84a57fa7636355d08b2f4e5cea2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340639"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="799da-102">Expressões lambda (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="799da-102">Lambda Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="799da-103">Uma expressão lambda é uma [função anônima](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que você pode usar para criar [delegados](../../../csharp/programming-guide/delegates/using-delegates.md) ou tipos de [árvore de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span><span class="sxs-lookup"><span data-stu-id="799da-103">A lambda expression is an [anonymous function](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) that you can use to create [delegates](../../../csharp/programming-guide/delegates/using-delegates.md) or [expression tree](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) types.</span></span> <span data-ttu-id="799da-104">Ao usar expressões lambda, você pode escrever funções locais que podem ser passadas como argumentos ou retornadas como o valor de chamadas de função.</span><span class="sxs-lookup"><span data-stu-id="799da-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="799da-105">Expressões lambda são particularmente úteis para escrever expressões de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="799da-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>  
  
 <span data-ttu-id="799da-106">Para criar uma expressão lambda, especifique os parâmetros de entrada (se houver) no lado esquerdo do operador lambda [=>](../../../csharp/language-reference/operators/lambda-operator.md) e coloque a expressão ou o bloco de instruções do outro lado.</span><span class="sxs-lookup"><span data-stu-id="799da-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="799da-107">Por exemplo, a expressão lambda `x => x * x` especifica um parâmetro chamado `x` e retorna o valor de `x` ao quadrado.</span><span class="sxs-lookup"><span data-stu-id="799da-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="799da-108">Você pode atribuir essa expressão a um tipo delegado como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="799da-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="799da-109">Para criar um tipo de árvore de expressão:</span><span class="sxs-lookup"><span data-stu-id="799da-109">To create an expression tree type:</span></span>  
  
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
  
 <span data-ttu-id="799da-110">O operador `=>` tem a mesma precedência que a atribuição (`=`) e é [associativo direito](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (consulte a seção "Associatividade" do artigo Operadores).</span><span class="sxs-lookup"><span data-stu-id="799da-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="799da-111">Lambdas são usadas em consultas [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] baseadas em métodos como argumentos para métodos de operador de consulta padrão como <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="799da-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="799da-112">Quando você usa a sintaxe baseada em método para chamar o método <xref:System.Linq.Enumerable.Where%2A> na classe <xref:System.Linq.Enumerable> (assim como você faz em [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] para objetos e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) o parâmetro é um tipo delegado <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="799da-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="799da-113">Uma expressão lambda é a maneira mais conveniente de criar esse delegado.</span><span class="sxs-lookup"><span data-stu-id="799da-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="799da-114">Quando você chama o mesmo método, por exemplo, na classe <xref:System.Linq.Queryable?displayProperty=nameWithType> (como faz em [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]), o tipo de parâmetro é uma <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\>, em que Func é qualquer delegado Func com até 16 parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="799da-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="799da-115">Novamente, uma expressão lambda é apenas uma maneira muito concisa de construir essa árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="799da-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="799da-116">Os lambdas permitem que chamadas `Where` pareçam semelhantes embora, na verdade, o tipo de objeto criado do lambda seja diferente.</span><span class="sxs-lookup"><span data-stu-id="799da-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="799da-117">No exemplo anterior, observe que a assinatura do delegado tem um parâmetro de entrada implícito inserido do tipo `int` e retorna um `int`.</span><span class="sxs-lookup"><span data-stu-id="799da-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="799da-118">A expressão lambda pode ser convertida como um delegado desse tipo porque também tem um parâmetro de entrada (`x`) e um valor de retorno que o compilador pode converter implicitamente no tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="799da-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="799da-119">(A inferência de tipos é discutida em mais detalhes nas seções a seguir.) Quando o delegado for chamado usando um parâmetro de entrada 5, ele retornará 25 como resultado.</span><span class="sxs-lookup"><span data-stu-id="799da-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="799da-120">Lambdas não são permitidas no lado esquerdo do operador [is](../../../csharp/language-reference/keywords/is.md) ou [as](../../../csharp/language-reference/keywords/as.md).</span><span class="sxs-lookup"><span data-stu-id="799da-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="799da-121">Todas as restrições que se aplicam a métodos anônimos também se aplicam às expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="799da-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="799da-122">Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="799da-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="799da-123">Lambdas de expressão</span><span class="sxs-lookup"><span data-stu-id="799da-123">Expression Lambdas</span></span>  
 <span data-ttu-id="799da-124">Uma expressão lambda com uma expressão no lado direito do operador => é chamada de *lambda de expressão*.</span><span class="sxs-lookup"><span data-stu-id="799da-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="799da-125">Os lambdas de expressão são usados amplamente na construção de [Árvores de expressão](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span><span class="sxs-lookup"><span data-stu-id="799da-125">Expression lambdas are used extensively in the construction of [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span></span> <span data-ttu-id="799da-126">Uma expressão lambda retorna o resultado da expressão e tem o seguinte formato básico:</span><span class="sxs-lookup"><span data-stu-id="799da-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>  
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="799da-127">Os parênteses serão opcionais somente se o lambda tiver um parâmetro de entrada; caso contrário, eles serão obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="799da-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="799da-128">Dois ou mais parâmetros de entrada são separados por vírgulas e envolvidos por parênteses:</span><span class="sxs-lookup"><span data-stu-id="799da-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="799da-129">Às vezes, é difícil ou impossível para o compilador inferir os tipos de entrada.</span><span class="sxs-lookup"><span data-stu-id="799da-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="799da-130">Quando isso ocorre, você pode especificar os tipos de maneira explícita conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="799da-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="799da-131">Especifique parâmetros de entrada zero com parênteses vazios:</span><span class="sxs-lookup"><span data-stu-id="799da-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="799da-132">Observe no exemplo anterior que o corpo de uma expressão lambda pode consistir de uma chamada de método.</span><span class="sxs-lookup"><span data-stu-id="799da-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="799da-133">No entanto, se você estiver criando árvores de expressão que serão avaliadas fora do .NET Framework, como no SQL Server, você não deverá usar chamadas de método em expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="799da-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="799da-134">Os métodos não terão significado fora do contexto do .NET Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="799da-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="799da-135">Lambdas de instrução</span><span class="sxs-lookup"><span data-stu-id="799da-135">Statement Lambdas</span></span>  
 <span data-ttu-id="799da-136">Um lambda de instrução lembra um lambda de expressão, exceto que as instruções estão incluídas entre chaves:</span><span class="sxs-lookup"><span data-stu-id="799da-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="799da-137">(parâmetros de entrada) => { instrução; }</span><span class="sxs-lookup"><span data-stu-id="799da-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="799da-138">O corpo de uma instrução lambda pode consistir de qualquer número de instruções; no entanto, na prática, normalmente não há mais de duas ou três.</span><span class="sxs-lookup"><span data-stu-id="799da-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="799da-139">Lambdas de instrução, como métodos anônimos, não podem ser usados para criar árvores de expressão.</span><span class="sxs-lookup"><span data-stu-id="799da-139">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="799da-140">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="799da-140">Async Lambdas</span></span>  
 <span data-ttu-id="799da-141">Você pode facilmente criar expressões e instruções lambda que incorporem processamento assíncrono, ao usar as palavras-chaves [async](../../../csharp/language-reference/keywords/async.md) e [await](../../../csharp/language-reference/keywords/await.md).</span><span class="sxs-lookup"><span data-stu-id="799da-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="799da-142">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="799da-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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

 <span data-ttu-id="799da-143">Você pode adicionar o mesmo manipulador de eventos ao usar um lambda assíncrono.</span><span class="sxs-lookup"><span data-stu-id="799da-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="799da-144">Para adicionar esse manipulador, adicione um modificador `async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="799da-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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

 <span data-ttu-id="799da-145">Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="799da-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="799da-146">Lambdas com os operadores de consulta padrão</span><span class="sxs-lookup"><span data-stu-id="799da-146">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="799da-147">Vários operadores de consulta padrão têm um parâmetro de entrada cujo tipo é de uma família <xref:System.Func%602> de delegados genéricos.</span><span class="sxs-lookup"><span data-stu-id="799da-147">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="799da-148">Esses delegados usam parâmetros de tipo para definir o número e os tipos de parâmetros de entrada e o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="799da-148">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="799da-149">delegados `Func` são muito úteis para encapsular expressões definidas pelo usuário aplicadas a cada elemento em um conjunto de dados de origem.</span><span class="sxs-lookup"><span data-stu-id="799da-149">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="799da-150">Por exemplo, considere o seguinte tipo delegado:</span><span class="sxs-lookup"><span data-stu-id="799da-150">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="799da-151">O delegado pode ser instanciado como `Func<int,bool> myFunc` onde `int` é um parâmetro de entrada e `bool` é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="799da-151">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="799da-152">O valor de retorno é sempre especificado no último parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="799da-152">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="799da-153">`Func<int, string, bool>` define um delegado com dois parâmetros de entrada, `int` e `string` e um tipo de retorno `bool`.</span><span class="sxs-lookup"><span data-stu-id="799da-153">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="799da-154">O delegado `Func` a seguir, quando é chamado, retornará true ou false para indicar se o parâmetro de entrada é igual a 5:</span><span class="sxs-lookup"><span data-stu-id="799da-154">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="799da-155">Você também pode fornecer uma expressão lambda quando o tipo de argumento é `Expression<Func>`, por exemplo, nos operadores de consulta padrão que são definidos em System.Linq.Queryable.</span><span class="sxs-lookup"><span data-stu-id="799da-155">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="799da-156">Quando você especifica um argumento `Expression<Func>`, o lambda será compilado em uma árvore de expressão.</span><span class="sxs-lookup"><span data-stu-id="799da-156">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="799da-157">Um operador de consulta padrão, o método <xref:System.Linq.Enumerable.Count%2A>, é mostrado aqui:</span><span class="sxs-lookup"><span data-stu-id="799da-157">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="799da-158">O compilador pode inferir o tipo de parâmetro de entrada ou você também pode especificá-lo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="799da-158">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="799da-159">Essa expressão lambda em particular conta esses inteiros (`n`) que, quando dividida por dois, tem um resto 1.</span><span class="sxs-lookup"><span data-stu-id="799da-159">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="799da-160">A linha de código a seguir gera uma sequência que contém todos os elementos na matriz `numbers` do lado esquerdo do 9 porque esse é o primeiro número na sequência que não atende à condição:</span><span class="sxs-lookup"><span data-stu-id="799da-160">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="799da-161">Este exemplo mostra como especificar vários parâmetros de entrada ao inclui-los entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="799da-161">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="799da-162">O método retorna todos os elementos na matriz de números até ser encontrado um número cujo valor seja menor do que sua posição.</span><span class="sxs-lookup"><span data-stu-id="799da-162">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="799da-163">Não confunda o operador lambda (`=>`) com o operador greater than ou equal (`>=`).</span><span class="sxs-lookup"><span data-stu-id="799da-163">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="799da-164">Inferência de tipos em lambdas</span><span class="sxs-lookup"><span data-stu-id="799da-164">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="799da-165">Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo lambda, no tipo delegado do parâmetro e em outros fatores conforme descrito na especificação da linguagem C#.</span><span class="sxs-lookup"><span data-stu-id="799da-165">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="799da-166">Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem.</span><span class="sxs-lookup"><span data-stu-id="799da-166">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="799da-167">Portanto, se você estiver consultando um `IEnumerable<Customer>`, a variável de entrada será inferida para ser um objeto `Customer`, o que significa que você tem acesso aos seus métodos e propriedades:</span><span class="sxs-lookup"><span data-stu-id="799da-167">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="799da-168">As regras gerais para lambdas são:</span><span class="sxs-lookup"><span data-stu-id="799da-168">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="799da-169">O lambda deve conter o mesmo número de parâmetros do tipo delegado.</span><span class="sxs-lookup"><span data-stu-id="799da-169">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="799da-170">Cada parâmetro de entrada no lambda deve ser implicitamente conversível em seu parâmetro delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="799da-170">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="799da-171">O valor de retorno do lambda (se houver) deve ser implicitamente conversível para o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="799da-171">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="799da-172">Observe que as expressões lambda em si não têm um tipo porque o sistema de tipo comum não possui conceito intrínseco da "expressão lambda".</span><span class="sxs-lookup"><span data-stu-id="799da-172">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="799da-173">No entanto, às vezes é conveniente falar informalmente do "tipo" de uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="799da-173">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="799da-174">Nesses casos, o tipo se refere ao tipo delegado ou tipo <xref:System.Linq.Expressions.Expression> ao qual a expressão lambda é convertida.</span><span class="sxs-lookup"><span data-stu-id="799da-174">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="799da-175">Escopo variável em expressões lambda</span><span class="sxs-lookup"><span data-stu-id="799da-175">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="799da-176">As lambdas podem se referir a *variáveis externas* (consulte [Métodos Anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) que estão no escopo do método que define a função lambda ou no escopo do tipo que contém a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="799da-176">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="799da-177">As variáveis que são capturadas dessa forma são armazenadas para uso na expressão lambda mesmo que de alguma outra forma elas saíssem do escopo e fossem coletadas como lixo.</span><span class="sxs-lookup"><span data-stu-id="799da-177">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="799da-178">Uma variável externa deve ser definitivamente atribuída para que possa ser consumida em uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="799da-178">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="799da-179">O exemplo a seguir demonstra estas regras:</span><span class="sxs-lookup"><span data-stu-id="799da-179">The following example demonstrates these rules:</span></span>  
  
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
  
 <span data-ttu-id="799da-180">As seguintes regras se aplicam ao escopo variável em expressões lambda:</span><span class="sxs-lookup"><span data-stu-id="799da-180">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="799da-181">Uma variável capturada não será coletada do lixo até que o delegado que faz referência a ela se qualifique para coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="799da-181">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="799da-182">As variáveis introduzidas em uma expressão lambda não são visíveis no método externo.</span><span class="sxs-lookup"><span data-stu-id="799da-182">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="799da-183">Uma expressão lambda não pode capturar um parâmetro `in`, `ref` ou `out` diretamente de um método delimitador.</span><span class="sxs-lookup"><span data-stu-id="799da-183">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="799da-184">Uma instrução return em uma expressão lambda não faz com que o método delimitador retorne.</span><span class="sxs-lookup"><span data-stu-id="799da-184">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="799da-185">Uma expressão lambda não poderá conter uma instrução `goto`, `break` ou `continue` que está dentro da função lambda se o destino da instrução jump estiver fora do bloco.</span><span class="sxs-lookup"><span data-stu-id="799da-185">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="799da-186">Também será um erro ter uma instrução jump fora do bloco da função lambda se o destino estiver dentro do bloco.</span><span class="sxs-lookup"><span data-stu-id="799da-186">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="799da-187">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="799da-187">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="799da-188">Capítulo do Livro em Destaque</span><span class="sxs-lookup"><span data-stu-id="799da-188">Featured Book Chapter</span></span>  
 <span data-ttu-id="799da-189">[Expressões lambda, eventos e delegados](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) em [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="799da-189">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799da-190">Consulte também</span><span class="sxs-lookup"><span data-stu-id="799da-190">See Also</span></span>  
 [<span data-ttu-id="799da-191">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="799da-191">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="799da-192">LINQ (Consulta Integrada à Linguagem)</span><span class="sxs-lookup"><span data-stu-id="799da-192">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="799da-193">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="799da-193">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="799da-194">is</span><span class="sxs-lookup"><span data-stu-id="799da-194">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="799da-195">Árvores de Expressão</span><span class="sxs-lookup"><span data-stu-id="799da-195">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="799da-196">Exemplos de C# do Visual Studio 2008 (veja os arquivos de exemplo de consultas LINQ e programa XQuery)</span><span class="sxs-lookup"><span data-stu-id="799da-196">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [<span data-ttu-id="799da-197">Expressões lambda recursivas</span><span class="sxs-lookup"><span data-stu-id="799da-197">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
