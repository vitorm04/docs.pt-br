---
title: Invocar UDFs Java do .NET para Apache Spark aplicativo
description: Saiba como chamar um UDF Java de um aplicativo .NET para Apache Spark.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e309a1e8cda2a559f300a07155c005677db85945
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877835"
---
# <a name="call-a-java-udf-from-your-net-for-apache-spark-application"></a><span data-ttu-id="63e78-103">Chamar um UDF Java de seu aplicativo .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="63e78-103">Call a Java UDF from your .NET for Apache Spark application</span></span>

<span data-ttu-id="63e78-104">Neste artigo, você aprenderá a chamar uma UDF (função de User-Defined Java) de seu aplicativo [.net para Apache Spark](https://github.com/dotnet/spark) .</span><span class="sxs-lookup"><span data-stu-id="63e78-104">In this article, you learn how to call a Java User-Defined Function (UDF) from your [.NET for Apache Spark](https://github.com/dotnet/spark) application.</span></span>

1. <span data-ttu-id="63e78-105">Como definir seus UDFs Java e compilá-los em um jar – essa etapa não será necessária se você já tiver um UDF definido em um arquivo jar.</span><span class="sxs-lookup"><span data-stu-id="63e78-105">How to define your Java UDFs and compile them into a jar - this step is not needed if you already have a UDF defined in a jar file.</span></span> <span data-ttu-id="63e78-106">Nesse caso, tudo o que você precisa é o nome completo da função UDF, incluindo o pacote.</span><span class="sxs-lookup"><span data-stu-id="63e78-106">In which case, all you need is the full name of the UDF function including the package.</span></span>
2. <span data-ttu-id="63e78-107">Registre e chame seu UDF Java em seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="63e78-107">Register and call your Java UDF in your .NET for Apache Spark application.</span></span>

## <a name="define-and-compile-your-java-udfs"></a><span data-ttu-id="63e78-108">Definir e compilar suas UDFs Java</span><span class="sxs-lookup"><span data-stu-id="63e78-108">Define and compile your Java UDFs</span></span>

1. <span data-ttu-id="63e78-109">Crie um projeto Maven ou SBT e adicione as seguintes dependências ao arquivo de configuração do projeto:</span><span class="sxs-lookup"><span data-stu-id="63e78-109">Create a Maven or SBT project and add the following dependencies into the project configuration file:</span></span>
    1. `org.apache.spark.spark-core_2.11.<version>`
    2. `org.apache.spark.spark-sql_2.11.<version>`
2. <span data-ttu-id="63e78-110">Defina seu UDF Java implementando a [interface relevante](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (de acordo com a assinatura de UDF) e importando o pacote relevante, conforme mostrado abaixo em um exemplo simples</span><span class="sxs-lookup"><span data-stu-id="63e78-110">Define your Java UDF by implementing the [relevant interface](https://github.com/apache/spark/blob/master/sql/core/src/main/java/org/apache/spark/sql/api/java/UDF1.java) (according to your UDF's signature) and importing the relevant package as shown below in a simple example</span></span>

    ```java
    package com.ScalaUdf.app; // Name of package where UDF is defined
    import org.apache.spark.sql.api.java.UDF1; // UDF interface to implement

    public class JavaUdf implements UDF1<Integer, Integer> { // Name of the Java UDF
        private static final int serialVersionUID = 1;
        @Override
        public Integer call(Integer num) throws Exception { // Define logic of UDF
            return (num + 5);
        }
    }
    ```

3. <span data-ttu-id="63e78-111">Compile e empacote seu projeto para criar e o JAR executável digamos `UdfApp-0.0.1.jar` .</span><span class="sxs-lookup"><span data-stu-id="63e78-111">Compile and package your project to create and executable jar say `UdfApp-0.0.1.jar`.</span></span>

## <a name="register-and-call-java-udfs-in-net-for-apache-spark"></a><span data-ttu-id="63e78-112">Registrar e chamar UDFs Java no .NET para Apache Spark</span><span class="sxs-lookup"><span data-stu-id="63e78-112">Register and call Java UDFs in .NET for Apache Spark</span></span>

1. <span data-ttu-id="63e78-113">Use a [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API para registrar seu UDF Java com o Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="63e78-113">Use the [`RegisterJava`](https://github.com/dotnet/spark/blob/8dcdcdc7c60d5f42cba5a90f1346d854ab5bf7bb/src/csharp/Microsoft.Spark/Sql/UDFRegistration.cs#L424) API to register your Java UDF with Spark SQL.</span></span>
2. <span data-ttu-id="63e78-114">Registre o `DataFrame` no qual você deseja chamar o UDF como uma tabela SQL usando a [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) função.</span><span class="sxs-lookup"><span data-stu-id="63e78-114">Register the `DataFrame` on which you want to call your UDF as an SQL Table using the [`CreateOrReplaceTempView`](https://github.com/dotnet/spark/blob/master/src/csharp/Microsoft.Spark/Sql/DataFrame.cs#L982) function.</span></span>
3. <span data-ttu-id="63e78-115">Use `SparkSession.Sql` para chamar o UDF na exibição de tabela usando o Spark SQL.</span><span class="sxs-lookup"><span data-stu-id="63e78-115">Use `SparkSession.Sql` to call the UDF on the table view using Spark SQL.</span></span>
<span data-ttu-id="63e78-116">Um exemplo básico para ilustrar as etapas acima:</span><span class="sxs-lookup"><span data-stu-id="63e78-116">A basic example to illustrate the above steps:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Scala/Java UDFs from .NET for Apache Spark")
                .GetOrCreate();
            spark.Udf().RegisterJava<int>("udfAdd5", "com.ScalaUdf.app.JavaUdf"); // Register your Java UDF as 'udfAdd5'
            DataFrame df = spark.CreateDataFrame(new int[] { 2, 5 });
            df.CreateOrReplaceTempView("numbersData"); // Create an SQL table from the DataFrame `df`
            DataFrame dfUdf = spark.Sql("SELECT udfAdd5(_1) As Result FROM numbersData"); // Call the registered UDF on the table
            dfUdf.Show();
            spark.Stop();
        }
    }
    ```

4. <span data-ttu-id="63e78-117">Envie este aplicativo usando `spark-submit` passando o jar Java UDF compilado anteriormente por meio da `--jars` opção:</span><span class="sxs-lookup"><span data-stu-id="63e78-117">Submit this application using `spark-submit` by passing the previously compiled Java UDF jar through the `--jars` option:</span></span>

    ```bash
    spark-submit --master local --jars UdfApp-0.0.1.jar --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-3.0.x-0.12.1.jar InterRuntimeUDFs.exe
    ```

    <span data-ttu-id="63e78-118">O `dfUdf` dataframe resultante tinha o número 5 adicionado a cada linha da coluna de entrada, conforme definido por `JavaUdf` :</span><span class="sxs-lookup"><span data-stu-id="63e78-118">The resultant `dfUdf` DataFrame had the number 5 added to each row of the input column as defined by `JavaUdf`:</span></span>

    ```text
    +-------+
    | Result|
    +-------+
    |      7|
    |     10|
    +-------+
    ```

## <a name="call-net-udf-from-scala-or-python-in-apache-spark"></a><span data-ttu-id="63e78-119">Chamar UDF .NET de escala ou Python no Apache Spark</span><span class="sxs-lookup"><span data-stu-id="63e78-119">Call .NET UDF from Scala or Python in Apache Spark</span></span>

<span data-ttu-id="63e78-120">Você também pode registrar e invocar um UDF em C# de um aplicativo Apache Spark escrito em escala ou Python usando [a ferramenta de código aberto sparkdotnetudf](https://github.com/imback82/sparkdotnetudf).</span><span class="sxs-lookup"><span data-stu-id="63e78-120">You can also register and invoke a C# UDF from an Apache Spark application written in Scala or Python using [the sparkdotnetudf open source tool](https://github.com/imback82/sparkdotnetudf).</span></span>
