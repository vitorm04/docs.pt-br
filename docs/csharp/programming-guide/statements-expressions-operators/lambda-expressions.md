---
title: "Express&#245;es lambda (Guia de Programa&#231;&#227;o em C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "expressões lambda [C#]"
  - "variáveis externas [C#]"
  - "instrução lambda [C#]"
  - "expressão lambda [C#]"
  - "expressões [c#], lambda"
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 64
caps.handback.revision: 64
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Express&#245;es lambda (Guia de Programa&#231;&#227;o em C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Uma expressão lambda é uma [função anônima](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) que você pode usar para criar [delegados](../../../csharp/programming-guide/delegates/using-delegates.md) ou [árvore de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md) tipos. Usando expressões lambda, você pode escrever funções locais que podem ser passadas como argumentos ou retornadas como o valor de chamadas de função. Expressões lambda são particularmente úteis para escrever expressões de consulta LINQ.  
  
 Para criar uma expressão lambda, você especifica parâmetros de entrada \(se houver\) no lado esquerdo do operador lambda [\= \>](../../../csharp/language-reference/operators/lambda-operator.md), e você coloca o bloco de expressão ou instrução do outro lado. Por exemplo, a expressão lambda `x => x * x` Especifica um parâmetro chamado `x` e retorna o valor de `x` ao quadrado. Você pode atribuir essa expressão a um tipo delegado, como mostra o exemplo a seguir:  
  
```c#  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 Para criar um tipo de árvore de expressão:  
  
```c#  
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
  
 O `=>` operador tem a mesma precedência de atribuição \(`=`\) e é [associativo direito](../../../csharp/programming-guide/statements-expressions-operators/operators.md) \(consulte a seção "Associatividade" do artigo operadores\).  
  
 Lambdas são usadas no método [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] consultas como argumentos para métodos operadores de consulta padrão como <xref:System.Linq.Enumerable.Where%2A>.  
  
 Quando você usa a sintaxe de método para chamar o <xref:System.Linq.Enumerable.Where%2A> método o <xref:System.Linq.Enumerable> classe \(como faria em [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] para objetos e [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]\) o parâmetro é um tipo delegado <xref:System.Func%602?displayProperty=fullName>. Uma expressão lambda é a maneira mais conveniente de criar esse delegado. Quando você chama o mesmo método, por exemplo, a <xref:System.Linq.Queryable?displayProperty=fullName> classe \(como faria em [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq_md.md)]\) e o tipo de parâmetro é um <xref:System.Linq.Expressions.Expression?displayProperty=fullName>\< Func \> onde Func é qualquer delegado Func com até 16 parâmetros de entrada. Novamente, uma expressão lambda é apenas uma maneira bem concisa de construir essa árvore de expressão. Os lambdas permitem que o `Where` chamadas pareçam semelhantes, embora na verdade o tipo de objeto criado do lambda seja diferente.  
  
 No exemplo anterior, observe que a assinatura do delegado possui um tipo implícito do parâmetro de tipo de entrada `int`, e retorna um `int`. A expressão lambda pode ser convertida em um delegado do tipo porque ele também tem um parâmetro de entrada \(`x`\) e um valor de retorno que o compilador pode converter implicitamente o tipo `int`. \(A inferência de tipos é discutida mais detalhadamente nas seções a seguir.\) Quando o representante é invocado usando um parâmetro de entrada de 5, ele retornará um resultado de 25.  
  
 Lambdas não são permitidos no lado esquerdo do [é](../../../csharp/language-reference/keywords/is.md) ou [como](../../../csharp/language-reference/keywords/as.md) operador.  
  
 Todas as restrições que se aplicam a métodos anônimos também se aplicam às expressões lambda. Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
## Lambdas de expressão  
 Uma expressão lambda com uma expressão no lado direito do \= \> operador é chamado um *expressão lambda*. Lambdas de expressão são usadas amplamente na construção de [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md). Uma expressão lambda retorna o resultado da expressão e usa o seguinte formato básico:  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
 Os parênteses são opcionais somente se o lambda tiver um parâmetro de entrada; Caso contrário, eles são necessários. Dois ou mais parâmetros de entrada são separados por vírgulas entre parênteses:  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
 Às vezes é difícil ou impossível para o compilador inferir os tipos de entrada. Quando isso ocorre, você pode especificar os tipos explicitamente, conforme mostrado no exemplo a seguir:  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
 Especifica parâmetros de entrada zero com parênteses vazios:  
  
<CodeContentPlaceHolder>5</CodeContentPlaceHolder>  
 Observe no exemplo anterior que o corpo de uma expressão lambda pode consistir de uma chamada de método. No entanto, se você estiver criando árvores de expressão são avaliadas fora do .NET Framework, como no SQL Server, você deverá não usar chamadas de método em expressões lambda. Os métodos não terão significado fora do contexto do .NET common language runtime.  
  
## Lambdas de instrução  
 Uma instrução lambda é semelhante a uma expressão lambda exceto que as instruções estão incluídas entre chaves:  
  
<CodeContentPlaceHolder>6</CodeContentPlaceHolder>  
 O corpo de uma instrução lambda pode consistir em qualquer número de instruções; No entanto, na prática há normalmente não mais do que dois ou três.  
  
<CodeContentPlaceHolder>7</CodeContentPlaceHolder>  
 Lambdas de instrução, como métodos anônimos, não podem ser usados para criar árvores de expressão.  
  
## Lambdas assíncronos  
 Você pode facilmente criar expressões lambda e instruções que incorporem processamento assíncrono usando o [async](../../../visual-basic/language-reference/modifiers/async.md) e [await](../../../csharp/language-reference/keywords/await.md) palavras\-chave. Por exemplo, o exemplo a seguir do Windows Forms contém um manipulador de eventos que chama e espera um método assíncrono, `ExampleMethodAsync`.  
  
<CodeContentPlaceHolder>8</CodeContentPlaceHolder>  
 Você pode adicionar o mesmo manipulador de eventos usando um lambda assíncrono. Para adicionar esse manipulador, adicione um `async` modificador antes da lista de parâmetro lambda, como mostra o exemplo a seguir.  
  
<CodeContentPlaceHolder>9</CodeContentPlaceHolder>  
 Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Lambdas com operadores de consulta padrão  
 Muitos operadores de consulta padrão têm um parâmetro de entrada cujo tipo é um do <xref:System.Func%602> família de delegados genéricos. Esses delegados usam parâmetros de tipo para definir o número e tipos de parâmetros de entrada e o tipo de retorno do delegado.`Func` delegados são muito úteis para encapsular expressões definidas pelo usuário que são aplicadas a cada elemento em um conjunto de dados de origem. Por exemplo, considere o seguinte tipo de delegado:  
  
```c#  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 O delegado pode ser instanciado como `Func<int,bool> myFunc` onde `int` é um parâmetro de entrada e `bool` é o valor de retorno. O valor de retorno é sempre especificado no último parâmetro de tipo.`Func<int, string, bool>` define um delegado com dois parâmetros de entrada, `int` e `string`, e um tipo de retorno de `bool`. O seguinte `Func` delegado, quando ele é chamado, retornará true ou false para indicar se o parâmetro de entrada é igual a 5:  
  
```c#  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 Você também pode fornecer uma expressão lambda quando o tipo de argumento é um `Expression<Func>`, por exemplo, em operadores de consulta padrão que são definidos em System.Linq.Queryable. Quando você especifica um `Expression<Func>` argumento, o lambda será compilado em uma árvore de expressão.  
  
 Um operador de consulta padrão, o <xref:System.Linq.Enumerable.Count%2A> método, é mostrado aqui:  
  
```c#  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 O compilador pode inferir o tipo de parâmetro de entrada, ou você também pode especificá\-lo explicitamente. Essa expressão lambda em particular conta esses inteiros \(`n`\) que quando dividida por dois tem um resto 1.  
  
 A linha de código a seguir gera uma sequência que contém todos os elementos de `numbers` matriz para o lado esquerdo do 9 porque esse é o primeiro número na sequência que não atende à condição:  
  
```c#  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 Este exemplo mostra como especificar vários parâmetros de entrada, colocando\-os entre parênteses. O método retorna todos os elementos na matriz de números até que um número é encontrado cujo valor é menor que sua posição. Não confunda o operador lambda \(`=>`\) com o operador maior que ou igual \(`>=`\).  
  
```c#  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## Inferência de tipos em Lambdas  
 Ao escrever lambdas, você geralmente não precisa especificar um tipo para os parâmetros de entrada porque o compilador pode inferir o tipo com base no corpo do lambda, o tipo do parâmetro delegado e outros fatores conforme descrito na especificação de linguagem c\#. Para a maioria dos operadores de consulta padrão, a primeira entrada é o tipo dos elementos na sequência de origem. Portanto, se você estiver consultando um `IEnumerable<Customer>`, em seguida, a variável de entrada é inferida para ser um `Customer` objeto, o que significa que você tem acesso a seus métodos e propriedades:  
  
```c#  
customers.Where(c => c.City == "London");  
```  
  
 As regras gerais para lambdas são os seguintes:  
  
-   O lambda deve conter o mesmo número de parâmetros do tipo delegado.  
  
-   Cada parâmetro de entrada no lambda deve ser implicitamente conversível para seu parâmetro delegado correspondente.  
  
-   O valor de retorno do lambda \(se houver\) deve ser implicitamente conversível para o tipo de retorno do delegado.  
  
 Observe que as expressões lambda em si não tem um tipo porque o common type system não tem nenhum conceito intrínseco da "expressão lambda". No entanto, às vezes é conveniente falar informalmente de "tipo" de uma expressão lambda. Nesses casos o tipo refere\-se ao tipo delegado ou <xref:System.Linq.Expressions.Expression> tipo ao qual a expressão lambda é convertida.  
  
## Escopo de variáveis em expressões Lambda  
 Lambdas podem se referir a *variáveis externas* \(consulte [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)\) que estão no escopo do método que define a função lambda ou no escopo do tipo que contém a expressão lambda. Variáveis que são capturadas dessa maneira são armazenados para uso na expressão lambda, mesmo se as variáveis de outra forma passariam fora do escopo e ser coletado como lixo. Uma variável externa deve ser definitivamente atribuída antes que ele possa ser consumido em uma expressão lambda. O exemplo a seguir demonstra estas regras:  
  
```c#  
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
  
-   Uma variável que é capturada será não ser lixo coletado até que o delegado que faz referência a ela se qualifique para coleta de lixo.  
  
-   As variáveis introduzidas em uma expressão lambda não são visíveis no método externo.  
  
-   Uma expressão lambda não pode capturar diretamente um `ref` ou `out` parâmetro de um método delimitador.  
  
-   Uma instrução de retorno em uma expressão lambda não faz com que o método delimitador retorne.  
  
-   Uma expressão lambda não pode conter um `goto` instrução `break` instrução, ou `continue` que está dentro da função lambda se o destino da instrução jump estiver fora do bloco. Também é um erro ter uma instrução jump fora do bloco de função lambda se o destino estiver dentro do bloco.  
  
## Especificação da Linguagem C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Capítulo do livro em destaque  
 [Delegados, eventos e expressões Lambda](http://go.microsoft.com/fwlink/?LinkId=195395) na [c\# 3.0 Cookbook, terceira edição: mais de 250 soluções para programadores de c\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
## Consulte também  
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [LINQ \(Consulta Integrada à Linguagem\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Métodos anônimos](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [Árvores de expressão](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Visual Studio 2008 amostras c\# \(Consulte arquivos de exemplos de consultas LINQ e XQuery\)](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)   
 [Expressões lambda recursivas](http://go.microsoft.com/fwlink/?LinkId=112395)