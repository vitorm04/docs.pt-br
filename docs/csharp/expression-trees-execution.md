---
title: Executar árvores de expressão
description: Saiba mais sobre como executar árvores de expressão, convertendo-as em instruções de IL (linguagem intermediária) executáveis.
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 54706cd5d8ebe60bb893bc82f05aecddae370602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218157"
---
# <a name="executing-expression-trees"></a>Executar árvores de expressão

[Anterior – Tipos de estruturas que dão suporte às árvores de expressão](expression-classes.md)

Uma *árvore de expressão* é uma estrutura de dados que representa algum código.
Ela não é código compilado nem executável. Se você quiser executar o código do .NET que é representado por uma árvore de expressão, é necessário convertê-lo em instruções IL executáveis. 
## <a name="lambda-expressions-to-functions"></a>Expressões lambda para funções
Você pode converter qualquer LambdaExpression ou qualquer tipo derivado de LambdaExpression em IL executável. Outros tipos de expressão não podem ser convertidos diretamente em código. Essa restrição tem pouco efeito na prática. As expressões lambda são os únicos tipos de expressões que você gostaria de executar convertendo em IL (linguagem intermediária) executável. (Pense no que significaria executar diretamente uma `ConstantExpression`. Significaria alguma coisa útil?) Qualquer árvore de expressão que é uma `LamdbaExpression` ou um tipo derivado de `LambdaExpression`, pode ser convertido em IL.
O tipo de expressão `Expression<TDelegate>` é o único exemplo concreto nas bibliotecas do .NET Core. Ele é usado para representar uma expressão que mapeia para qualquer tipo delegado. Como esse tipo mapeia para um tipo delegado, o .NET pode examinar a expressão e gerar a IL para um delegado apropriado que corresponda à assinatura da expressão lambda. 

Na maioria dos casos, isso cria um mapeamento simples entre uma expressão e o delegado correspondente. Por exemplo, uma árvore de expressão que é representada por `Expression<Func<int>>` seria convertida em um delegado do tipo `Func<int>`. Para uma expressão lambda com qualquer tipo de retorno e lista de argumentos, existe um tipo delegado que é o tipo de destino para o código executável representado por essa expressão lamdba.

O tipo `LamdbaExpression` contém membros `Compile` e `CompileToMethod` que você usaria para converter uma árvore de expressão em código executável. O método `Compile` cria um delegado. O método `CompileToMethod` atualiza um objeto `MethodBuilder` com a IL que representa a saída compilada da árvore de expressão. Observe que `CompileToMethod` só está disponível na estrutura de área de trabalho completa e não na estrutura do .NET Core.

Opcionalmente, você também pode fornecer um `DebugInfoGenerator` que receberá as informações de depuração de símbolo para o objeto delegado gerado. Isso permite que você converta a árvore de expressão em um objeto delegado e tenha as informações de depuração completas sobre o delegado gerado.

Uma expressão seria convertida em um delegado usando o seguinte código:

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

Observe que o tipo delegado se baseia no tipo de expressão. Você deve conhecer o tipo de retorno e a lista de argumentos se quiser usar o objeto delegado de maneira fortemente tipada. O método `LambdaExpression.Compile()` retorna o tipo `Delegate`. Você precisará convertê-lo para o tipo delegado correto para fazer com que as ferramentas de tempo de compilação verifiquem a lista de argumentos do tipo de retorno.

## <a name="execution-and-lifetimes"></a>Execução e tempos de vida

O código é executado ao invocar o delegado que foi criado quando você chamou `LamdbaExpression.Compile()`. Você pode ver isso acima do local em que `add.Compile()` retorna um delegado. Invocar o delegado, chamando `func()`, executa o código.

Esse delegado representa o código na árvore de expressão. Você pode reter o identificador para esse delegado e invocá-lo mais tarde. Você não precisa compilar a árvore de expressão sempre que deseja executar o código que ela representa. (Lembre-se que as árvores de expressão são imutáveis e compilar a mesma árvore de expressão mais tarde, criará um delegado que executa o mesmo código).

Eu alerto contra a tentativa de criar mecanismos de cache mais sofisticados para aumentar o desempenho ao evitar chamadas de compilação desnecessárias. A comparação de duas árvores de expressão arbitrárias para determinar se elas representam o mesmo algoritmo também será algo demorado para executar. Provavelmente você descobrirá que o tempo de computação economizado para evitar quaisquer chamadas extras à `LambdaExpression.Compile()` será mais demorado que o tempo da execução do código que determina se duas árvores de expressão diferentes resultam no mesmo código executável.

## <a name="caveats"></a>Advertências

A compilação de uma expressão lambda para um delegado e invocar esse delegado é uma das operações mais simples que você pode realizar com uma árvore de expressão. No entanto, mesmo com essa operação simples, há limitações que você deve estar ciente. 

As expressões lambda criam fechamentos sobre todas as variáveis locais que são referenciadas na expressão. Você deve assegurar que todas as variáveis que farão parte do delegado são utilizáveis no local em que você chamar `Compile` e no momento em que você executar o delegado resultante.

Em geral, o compilador garantirá que isso seja verdadeiro. No entanto, se sua expressão acessa uma variável que implementa `IDisposable`, é possível que seu código descarte o objeto enquanto ele ainda é mantido pela árvore de expressão.

Por exemplo, esse código funciona bem, porque `int` não implementa `IDisposable`:

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

O delegado capturou uma referência à variável local `constant`.
Essa variável é acessada a qualquer momento mais tarde, quando a função retornada por `CreateBoundFunc` for executada.

No entanto, considere essa classe (bastante artificial) que implementa `IDisposable`:

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

Ao usá-la em uma expressão, como mostrado abaixo, você obterá uma `ObjectDisposedException` ao executar o código referenciado pela propriedade `Resource.Argument`:

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

O delegado retornado desse método fechou sobre o objeto `constant`, que foi descartado. (Foi descartado, porque foi declarado em uma instrução `using`). 

Agora, ao executar o delegado retornado desse método, uma `ObjecctDisposedException` será lançada no ponto de execução.

Parece realmente estranho ter um erro de tempo de execução que representa um constructo de tempo de compilação, mas esse é o mundo em que entramos quando trabalhamos com árvores de expressão.

Há muitas permutações desse problema, portanto é difícil oferecer diretrizes gerais para evitá-lo. Tenha cuidado ao acessar variáveis locais quando estiver definindo expressões e tenha cuidado ao acessar o estado no objeto atual (representado por `this`) quando estiver criando uma árvore de expressão que pode ser retornada por uma API pública.

O código na sua expressão pode referenciar métodos ou propriedades em outros assemblies. Esse assembly deve estar acessível quando a expressão for definida, quando ela for compilada e quando o delegado resultante for chamado. Você vai se deparar com uma `ReferencedAssemblyNotFoundException` nos casos em que ele não estiver presente.

## <a name="summary"></a>Resumo

As árvores de expressão que representam expressões lambda podem ser compiladas para criar um delegado que pode ser executado. Isso fornece um mecanismo para executar o código representado por uma árvore de expressão.

A árvore de expressão representa o código que seria executado para qualquer constructo específico que você criar. Contanto que o ambiente em que você compilar e executar o código corresponda ao ambiente em que você criar a expressão, tudo funcionará conforme o esperado. Quando isso não acontece, os erros são bastante previsíveis e serão capturados em seus primeiros testes de qualquer código usando as árvores de expressão.

[Próximo – Interpretando expressões](expression-trees-interpreting.md)
