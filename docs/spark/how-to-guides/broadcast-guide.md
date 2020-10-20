---
title: Usar variáveis de difusão no .NET para Apache Spark
description: Saiba como usar variáveis de difusão no .NET para aplicativos Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 55a52754439020bd2a925aa3e987fb4ad99c9c3d
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223997"
---
# <a name="use-broadcast-variables-in-net-for-apache-spark"></a><span data-ttu-id="3999e-103">Usar variáveis de difusão no .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3999e-103">Use broadcast variables in .NET for Apache Spark</span></span>

<span data-ttu-id="3999e-104">Neste artigo, você aprenderá a usar variáveis de difusão no .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="3999e-104">In this article, you learn how to use broadcast variables in .NET for Apache Spark.</span></span> <span data-ttu-id="3999e-105">As [variáveis de difusão no Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) são mecanismos para compartilhar variáveis em executores que se destinam a ser somente leitura.</span><span class="sxs-lookup"><span data-stu-id="3999e-105">[Broadcast variables in Apache Spark](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) are mechanisms for sharing variables across executors that are meant to be read-only.</span></span> <span data-ttu-id="3999e-106">As variáveis de difusão permitem manter uma variável somente leitura armazenada em cache em cada máquina, em vez de enviar uma cópia dela com tarefas.</span><span class="sxs-lookup"><span data-stu-id="3999e-106">Broadcast variables allow you to keep a read-only variable cached on each machine rather than shipping a copy of it with tasks.</span></span> <span data-ttu-id="3999e-107">Você pode usar variáveis de difusão para dar a cada nó uma cópia de um conjunto de dados de entrada grande de maneira eficiente.</span><span class="sxs-lookup"><span data-stu-id="3999e-107">You can use broadcast variables to give every node a copy of a large input dataset in an efficient manner.</span></span>

<span data-ttu-id="3999e-108">Como os dados são enviados apenas uma vez, as variáveis de difusão têm benefícios de desempenho quando comparadas com as variáveis locais que são enviadas aos executores com cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="3999e-108">Because the data is sent only once, broadcast variables have performance benefits when compared to local variables that are shipped to the executors with each task.</span></span> <span data-ttu-id="3999e-109">Consulte a [documentação da variável de difusão oficial](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) para obter uma compreensão mais profunda das variáveis de difusão e por que elas são usadas.</span><span class="sxs-lookup"><span data-stu-id="3999e-109">Refer to the [official broadcast variable documentation](https://spark.apache.org/docs/2.2.0/rdd-programming-guide.html#broadcast-variables) to get a deeper understanding of broadcast variables and why they are used.</span></span>

## <a name="create-broadcast-variables"></a><span data-ttu-id="3999e-110">Criar variáveis de difusão</span><span class="sxs-lookup"><span data-stu-id="3999e-110">Create broadcast variables</span></span>

<span data-ttu-id="3999e-111">Para criar uma variável de difusão, chame `SparkContext.Broadcast(v)` para qualquer variável `v` .</span><span class="sxs-lookup"><span data-stu-id="3999e-111">To create a broadcast variable, call `SparkContext.Broadcast(v)` for any variable `v`.</span></span> <span data-ttu-id="3999e-112">A variável de difusão é um wrapper em volta da variável `v` e seu valor pode ser acessado chamando o `Value()` método.</span><span class="sxs-lookup"><span data-stu-id="3999e-112">The broadcast variable is a wrapper around the variable `v`, and its value can be accessed by calling the `Value()` method.</span></span>

<span data-ttu-id="3999e-113">No trecho de código a seguir, uma variável de cadeia de caracteres `v` é criada e uma variável de difusão `bv` é criada quando `SparkContext.Broadcast(v)` é chamado.</span><span class="sxs-lookup"><span data-stu-id="3999e-113">In the following code snippet, a string variable `v` is created, and a broadcast variable `bv` is created when `SparkContext.Broadcast(v)`is called.</span></span> <span data-ttu-id="3999e-114">Observe que o parâmetro de tipo para `Broadcast` , String, corresponde ao tipo da variável que está sendo transmitida.</span><span class="sxs-lookup"><span data-stu-id="3999e-114">Notice the type parameter for `Broadcast`, string, matches the type of the variable being broadcasted.</span></span> <span data-ttu-id="3999e-115">A UDF (função definida pelo usuário) retorna o valor de `bv` .</span><span class="sxs-lookup"><span data-stu-id="3999e-115">The user-defined function (UDF) returns the value of `bv`.</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

Func<Column, Column> udf = Udf<string, string>(
    str => $"{str}: {bv.Value()}");
```

## <a name="delete-broadcast-variables"></a><span data-ttu-id="3999e-116">Excluir variáveis de difusão</span><span class="sxs-lookup"><span data-stu-id="3999e-116">Delete broadcast variables</span></span>

<span data-ttu-id="3999e-117">A variável de difusão pode ser excluída de todos os executores chamando o `Destroy()` método.</span><span class="sxs-lookup"><span data-stu-id="3999e-117">The broadcast variable can be deleted from all executors by calling the `Destroy()` method.</span></span>

```csharp
bv.Destroy();
```

<span data-ttu-id="3999e-118">`Destroy()` exclui todos os dados e metadados relacionados à variável de difusão e devem ser usados com cautela.</span><span class="sxs-lookup"><span data-stu-id="3999e-118">`Destroy()` deletes all data and metadata related to the broadcast variable and should be used with caution.</span></span> <span data-ttu-id="3999e-119">Depois que uma variável de difusão é destruída, ela não pode ser usada novamente.</span><span class="sxs-lookup"><span data-stu-id="3999e-119">Once a broadcast variable is destroyed, it can't be used again.</span></span>

## <a name="limit-broadcast-variable-scope-in-udfs"></a><span data-ttu-id="3999e-120">Limitar o escopo da variável de difusão em UDFs</span><span class="sxs-lookup"><span data-stu-id="3999e-120">Limit broadcast variable scope in UDFs</span></span>

<span data-ttu-id="3999e-121">Ao usar variáveis de difusão em UDFs, você precisa limitar o escopo da variável somente ao UDF que está fazendo referência à variável.</span><span class="sxs-lookup"><span data-stu-id="3999e-121">When you use broadcast variables in UDFs, you need to limit the scope of the variable to only the UDF that is referencing the variable.</span></span> <span data-ttu-id="3999e-122">O [guia para usar UDFs](udf-guide.md) descreve esse fenômeno em detalhes.</span><span class="sxs-lookup"><span data-stu-id="3999e-122">The [guide to using UDFs](udf-guide.md) describes this phenomenon in detail.</span></span> <span data-ttu-id="3999e-123">O escopo é especialmente crucial quando você chama `Destroy()` na variável de difusão.</span><span class="sxs-lookup"><span data-stu-id="3999e-123">Scope is especially crucial when you call `Destroy()` on the broadcast variable.</span></span>

<span data-ttu-id="3999e-124">Se a variável de difusão que foi destruída estiver visível ou acessível de outros UDFs, ela será selecionada para a serialização por todas as UDFs, mesmo se não estiver sendo referenciada por elas.</span><span class="sxs-lookup"><span data-stu-id="3999e-124">If the broadcast variable that has been destroyed is visible to or accessible from other UDFs, it gets picked up for serialization by all of the UDFs, even if it is not being referenced by them.</span></span> <span data-ttu-id="3999e-125">O .NET para Apache Spark não pode serializar a variável de difusão destruída, o que resulta em um erro.</span><span class="sxs-lookup"><span data-stu-id="3999e-125">.NET for Apache Spark is unable to serialize the destroyed broadcast variable, which results in an error.</span></span> <span data-ttu-id="3999e-126">O trecho de código a seguir demonstra esse erro:</span><span class="sxs-lookup"><span data-stu-id="3999e-126">The following code snippet demonstrates this error:</span></span>

```csharp
string v = "Variable to be broadcasted";
Broadcast<string> bv = SparkContext.Broadcast(v);

// Using the broadcast variable in a UDF:
Func<Column, Column> udf1 = Udf<string, string>(
    str => $"{str}: {bv.Value()}");

// Destroying bv
bv.Destroy();

// Calling udf1 after destroying bv throws the following expected exception:
// org.apache.spark.SparkException: Attempted to use Broadcast(0) after it was destroyed
df.Select(udf1(df["_1"])).Show();

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 throws the following (unexpected) exception:
// [Error] [JvmBridge] org.apache.spark.SparkException: Task not serializable
df.Select(udf2(df["_1"])).Show();
```

<span data-ttu-id="3999e-127">O trecho de código a seguir demonstra como garantir que a destruição `bv` não afete `udf2` devido a um comportamento de serialização inesperado:</span><span class="sxs-lookup"><span data-stu-id="3999e-127">The following code snippet demonstrates how to ensure that destroying `bv` doesn't affect `udf2` because of an unexpected serialization behavior:</span></span>

```csharp
string v = "Variable to be broadcasted";
// Restricting the visibility of bv to only the UDF referencing it
{
    Broadcast<string> bv = SparkContext.Broadcast(v);

    // Using the broadcast variable in a UDF:
    Func<Column, Column> udf1 = Udf<string, string>(
        str => $"{str}: {bv.Value()}");

    // Destroying bv
    bv.Destroy();
}

// Different UDF udf2 that is not referencing bv
Func<Column, Column> udf2 = Udf<string, string>(
    str => $"{str}: not referencing broadcast variable");

// Calling udf2 works fine as expected
df.Select(udf2(df["_1"])).Show();
```

## <a name="next-steps"></a><span data-ttu-id="3999e-128">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="3999e-128">Next steps</span></span>

* [<span data-ttu-id="3999e-129">Introdução ao .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="3999e-129">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="3999e-130">Depurar um aplicativo .NET para Apache Spark no Windows</span><span class="sxs-lookup"><span data-stu-id="3999e-130">Debug a .NET for Apache Spark application on Windows</span></span>](debug.md)
* [<span data-ttu-id="3999e-131">Implantar .NET para Apache Spark trabalho e binários de função definidos pelo usuário</span><span class="sxs-lookup"><span data-stu-id="3999e-131">Deploy .NET for Apache Spark worker and user-defined function binaries</span></span>](deploy-worker-udf-binaries.md)
