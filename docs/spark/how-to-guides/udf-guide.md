---
title: Criar funções definidas pelo usuário (UDF) no .NET para Apache Spark
description: Saiba como implementar o UDF (funções definidas pelo usuário) no .NET para aplicativos Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 50e631b0c561ebdf081d4c1b7d16bf25abb322e5
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224182"
---
# <a name="create-user-defined-functions-udf-in-net-for-apache-spark"></a><span data-ttu-id="af134-103">Criar funções definidas pelo usuário (UDF) no .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="af134-103">Create user-defined functions (UDF) in .NET for Apache Spark</span></span>

<span data-ttu-id="af134-104">Neste artigo, você aprenderá a usar o UDF (funções definidas pelo usuário) no .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="af134-104">In this article, you learn how to use user-defined functions (UDF) in .NET for Apache Spark.</span></span> <span data-ttu-id="af134-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) o é um recurso do Spark que permite usar funções personalizadas para estender a funcionalidade interna do sistema.</span><span class="sxs-lookup"><span data-stu-id="af134-105">[UDFs)](https://spark.apache.org/docs/latest/api/java/org/apache/spark/sql/expressions/UserDefinedFunction.html) are a Spark feature that allow you to use custom functions to extend the system's built-in functionality.</span></span> <span data-ttu-id="af134-106">Os UDFs transformam valores de uma única linha dentro de uma tabela para produzir um único valor de saída correspondente por linha com base na lógica definida no UDF.</span><span class="sxs-lookup"><span data-stu-id="af134-106">UDFs transform values from a single row within a table to produce a single corresponding output value per row based on the logic defined in the UDF.</span></span>

## <a name="define-udfs"></a><span data-ttu-id="af134-107">Definir UDFs</span><span class="sxs-lookup"><span data-stu-id="af134-107">Define UDFs</span></span>

<span data-ttu-id="af134-108">Examine a seguinte definição de UDF:</span><span class="sxs-lookup"><span data-stu-id="af134-108">Review the following UDF definition:</span></span>

```csharp
string s1 = "hello";
Func<Column, Column> udf = Udf<string, string>(
    str => $"{s1} {str}");
```

<span data-ttu-id="af134-109">O UDF usa uma `string` como entrada na forma de uma [coluna](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) de um [dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)e retorna um `string` com `hello` anexado na frente da entrada.</span><span class="sxs-lookup"><span data-stu-id="af134-109">The UDF takes a `string` as an input in the form of a [Column](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Column.cs#L14) of a [Dataframe](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L24)) and returns a `string` with `hello` appended in front of the input.</span></span>

<span data-ttu-id="af134-110">O dataframe a seguir `df` contém uma lista de nomes:</span><span class="sxs-lookup"><span data-stu-id="af134-110">The following DataFrame `df` contains a list of names:</span></span>

```text
+-------+
|   name|
+-------+
|Michael|
|   Andy|
| Justin|
+-------+
```

<span data-ttu-id="af134-111">Agora, vamos aplicar o definido acima `udf` ao dataframe `df` :</span><span class="sxs-lookup"><span data-stu-id="af134-111">Now let's apply the above defined `udf` to the DataFrame `df`:</span></span>

```csharp
DataFrame udfResult = df.Select(udf(df["name"]));
```

<span data-ttu-id="af134-112">O dataframe a seguir `udfResult` é o resultado do UDF:</span><span class="sxs-lookup"><span data-stu-id="af134-112">The following DataFrame `udfResult` is the result of the UDF:</span></span>

```text
+-------------+
|         name|
+-------------+
|hello Michael|
|   hello Andy|
| hello Justin|
+-------------+
```

<span data-ttu-id="af134-113">Para entender melhor como implementar UDFs, examine as [funções auxiliares UDF](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) e [exemplos](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) no github.</span><span class="sxs-lookup"><span data-stu-id="af134-113">To better understand how to implement UDFs, review the [UDF helper functions](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/Functions.cs#L3616) and [examples](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark.E2ETest/UdfTests/UdfSimpleTypesTests.cs#L49) on GitHub.</span></span>

## <a name="udf-serialization"></a><span data-ttu-id="af134-114">Serialização de UDF</span><span class="sxs-lookup"><span data-stu-id="af134-114">UDF serialization</span></span>

<span data-ttu-id="af134-115">Como as UDFs são funções que precisam ser executadas em trabalhadores, elas precisam ser serializadas e enviadas aos trabalhadores como parte da carga do driver.</span><span class="sxs-lookup"><span data-stu-id="af134-115">Because UDFs are functions that need to be executed on workers, they have to be serialized and sent to the workers as part of the payload from the driver.</span></span> <span data-ttu-id="af134-116">O [delegado](../../csharp/programming-guide/delegates/index.md), que é uma referência ao método, precisa ser serializado, bem como seu [destino](xref:System.Delegate.Target%2A), que é a instância de classe na qual o delegado atual invoca o método de instância.</span><span class="sxs-lookup"><span data-stu-id="af134-116">The [delegate](../../csharp/programming-guide/delegates/index.md), which is a reference to the method, needs to be serialized as well as its [target](xref:System.Delegate.Target%2A), which is the class instance on which the current delegate invokes the instance method.</span></span> <span data-ttu-id="af134-117">Examine este [exemplo de código no GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) para entender melhor como a serialização UDF está sendo feita.</span><span class="sxs-lookup"><span data-stu-id="af134-117">Review this [code example in GitHub](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Utils/CommandSerDe.cs#L149) to get a better understanding of how UDF serialization is being done.</span></span>

<span data-ttu-id="af134-118">O .NET para Apache Spark usa o .NET Core, que não dá suporte a delegados de serialização.</span><span class="sxs-lookup"><span data-stu-id="af134-118">.NET for Apache Spark uses .NET Core, which doesn't support serializing delegates.</span></span> <span data-ttu-id="af134-119">Em vez disso, a reflexão é usada para serializar o destino onde o delegado é definido.</span><span class="sxs-lookup"><span data-stu-id="af134-119">Instead, reflection is used to serialize the target where the delegate is defined.</span></span> <span data-ttu-id="af134-120">Quando vários delegados são definidos em um escopo comum, eles têm um fechamento compartilhado que se torna o destino de reflexão para serialização.</span><span class="sxs-lookup"><span data-stu-id="af134-120">When multiple delegates are defined in a common scope, they have a shared closure that becomes the target of reflection for serialization.</span></span>

### <a name="serialization-example"></a><span data-ttu-id="af134-121">Exemplo de serialização</span><span class="sxs-lookup"><span data-stu-id="af134-121">Serialization example</span></span>

<span data-ttu-id="af134-122">O trecho de código a seguir define duas variáveis String que estão sendo referenciadas em dois delegados de função que retornam as respectivas cadeias de caracteres como resultado:</span><span class="sxs-lookup"><span data-stu-id="af134-122">The following code snippet defines two string variables that are being referenced in two function delegates that return the respective strings as a result:</span></span>

```csharp
using System;

public class C {
    public void M() {
        string s1 = "s1";
        string s2 = "s2";
        Func<string, string> a = str => s1;
        Func<string, string> b = str => s2;
    }
}
```

<span data-ttu-id="af134-123">O código C# acima gera o seguinte código de desmontagem de C# (fonte de crédito: [sharplab.Io](https://sharplab.io)) do compilador:</span><span class="sxs-lookup"><span data-stu-id="af134-123">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        public string s2;

        internal string <M>b__0(string str)
        {
            return s1;
        }

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        <>c__DisplayClass0_.s2 = "s2";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_.<M>b__1);
    }
}
```

<span data-ttu-id="af134-124">Ambos `func` e `func2` compartilham o mesmo fechamento `<>c__DisplayClass0_0` , que é o destino que é serializado ao serializar os delegados `func` e `func2` .</span><span class="sxs-lookup"><span data-stu-id="af134-124">Both `func` and `func2` share the same closure `<>c__DisplayClass0_0`, which is the target that is serialized when serializing the delegates `func` and `func2`.</span></span> <span data-ttu-id="af134-125">Embora `Func<string, string> a` o só faça referência a `s1` , `s2` o também é serializado quando os bytes são enviados aos trabalhadores.</span><span class="sxs-lookup"><span data-stu-id="af134-125">Even though `Func<string, string> a` is only referencing `s1`, `s2` is also serialized when the bytes are sent to the workers.</span></span>

<span data-ttu-id="af134-126">Isso pode levar a alguns comportamentos inesperados no tempo de execução (como no caso do uso de [variáveis de difusão](broadcast-guide.md)), motivo pelo qual é recomendável restringir a visibilidade das variáveis usadas em uma função para o escopo dessa função.</span><span class="sxs-lookup"><span data-stu-id="af134-126">This can lead to some unexpected behaviors at runtime (like in the case of using [broadcast variables](broadcast-guide.md)), which is why we recommend that you restrict the visibility of the variables used in a function to that function's scope.</span></span>

<span data-ttu-id="af134-127">O trecho de código a seguir é a maneira recomendada para implementar o comportamento de serialização desejado:</span><span class="sxs-lookup"><span data-stu-id="af134-127">The following code snippet is the recommended way to implement the desired serialization behavior:</span></span>

```csharp
using System;

public class C {
    public void M() {
        {
            string s1 = "s1";
            Func<string, string> a = str => s1;
        }
        {
            string s2 = "s2";
            Func<string, string> b = str => s2;
        }
    }
}
```

<span data-ttu-id="af134-128">O código C# acima gera o seguinte código de desmontagem de C# (fonte de crédito: [sharplab.Io](https://sharplab.io)) do compilador:</span><span class="sxs-lookup"><span data-stu-id="af134-128">The above C# code generates the following C# disassembly (credit source: [sharplab.io](https://sharplab.io)) code from the compiler:</span></span>

```csharp
public class C
{
    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_0
    {
        public string s1;

        internal string <M>b__0(string str)
        {
            return s1;
        }
    }

    [CompilerGenerated]
    private sealed class <>c__DisplayClass0_1
    {
        public string s2;

        internal string <M>b__1(string str)
        {
            return s2;
        }
    }

    public void M()
    {
        <>c__DisplayClass0_0 <>c__DisplayClass0_ = new <>c__DisplayClass0_0();
        <>c__DisplayClass0_.s1 = "s1";
        Func<string, string> func = new Func<string, string>(<>c__DisplayClass0_.<M>b__0);
        <>c__DisplayClass0_1 <>c__DisplayClass0_2 = new <>c__DisplayClass0_1();
        <>c__DisplayClass0_2.s2 = "s2";
        Func<string, string> func2 = new Func<string, string>(<>c__DisplayClass0_2.<M>b__1);
    }
}
```

<span data-ttu-id="af134-129">Observe que `func` e `func2` não compartilha mais um fechamento e eles têm seus próprios fechamentos separados `<>c__DisplayClass0_0` e, `<>c__DisplayClass0_1` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="af134-129">Notice that `func` and `func2` no longer share a closure, and they have their own separate closures `<>c__DisplayClass0_0` and `<>c__DisplayClass0_1` respectively.</span></span> <span data-ttu-id="af134-130">Quando usado como o destino para serialização, nada além das variáveis referenciadas será serializado para o delegado.</span><span class="sxs-lookup"><span data-stu-id="af134-130">When used as the target for serialization, nothing other than the referenced variables will get serialized for the delegate.</span></span> <span data-ttu-id="af134-131">Esse comportamento é importante para se ter em mente ao implementar vários UDFs em um escopo comum.</span><span class="sxs-lookup"><span data-stu-id="af134-131">This behavior is important to keep in mind while implementing multiple UDFs in a common scope.</span></span>

## <a name="some-spark-udf-caveats"></a><span data-ttu-id="af134-132">Algumas advertências de UDF do Spark</span><span class="sxs-lookup"><span data-stu-id="af134-132">Some Spark UDF caveats</span></span>

* <span data-ttu-id="af134-133">Valores nulos em UDFs podem gerar exceções.</span><span class="sxs-lookup"><span data-stu-id="af134-133">Null values in UDFs can throw exceptions.</span></span> <span data-ttu-id="af134-134">É responsabilidade do desenvolvedor tratá-los.</span><span class="sxs-lookup"><span data-stu-id="af134-134">It's the responsibility of the developer to handle them.</span></span>
* <span data-ttu-id="af134-135">As UDFs não aproveitam as otimizações fornecidas pelas funções internas do Spark, portanto, é recomendável usar funções internas sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="af134-135">UDFs don't leverage the optimizations provided by Spark's built-in functions, so it's recommended to use built-in functions where possible.</span></span>

## <a name="faqs"></a><span data-ttu-id="af134-136">Perguntas frequentes</span><span class="sxs-lookup"><span data-stu-id="af134-136">FAQs</span></span>

<span data-ttu-id="af134-137">**Por que obtenho o erro `System.NotImplementedException: The method or operation is not implemented.` ou `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` ao tentar chamar um UDF com o `ArrayType` `MapType` `ArrayList` `HashTable` argumento ou o tipo de retorno?**</span><span class="sxs-lookup"><span data-stu-id="af134-137">**Why do I get the error `System.NotImplementedException: The method or operation is not implemented.` or `System.InvalidCastException: Unable to cast object of type 'System.Collections.Hashtable' to type 'System.Collections.Generic.IDictionary` when trying to call a UDF with `ArrayType`, `MapType`, `ArrayList`, or `HashTable` as argument or return type?**</span></span>  
<span data-ttu-id="af134-138">O suporte para `ArrayType` e `MapType` não é fornecido até [v 1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0)e, portanto, você receberá esse erro se estiver usando um .net para Apache Spark versão anterior a ele e tentar passar esses tipos como argumentos para o UDF ou como um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="af134-138">Support for `ArrayType` and `MapType` is not provided until [v1.0](https://github.com/dotnet/spark/releases/tag/v1.0.0), and so you would get this error if using a .NET for Apache Spark version prior to that, and trying to pass these types either as arguments to the UDF or as a return type.</span></span>
<span data-ttu-id="af134-139">`ArrayList` os `HashTable` tipos e não podem ser suportados como tipos de retorno de um UDF, pois são coleções não genéricas e, portanto, suas definições de tipo de elemento não podem ser fornecidas para o Spark.</span><span class="sxs-lookup"><span data-stu-id="af134-139">`ArrayList` and `HashTable` types cannot be supported as return types of a UDF as they are non-generic collections and hence their element type definitions cannot be provided to Spark.</span></span>

## <a name="next-steps"></a><span data-ttu-id="af134-140">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="af134-140">Next steps</span></span>

* [<span data-ttu-id="af134-141">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="af134-141">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="af134-142">Depurar um aplicativo .NET para Apache Spark no Windows</span><span class="sxs-lookup"><span data-stu-id="af134-142">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
