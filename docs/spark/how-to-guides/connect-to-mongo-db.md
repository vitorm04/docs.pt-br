---
title: Conectar o .NET para Apache Spark ao MongoDB
description: Saiba como se conectar à sua instância do MongoDB de seu aplicativo .NET para Apache Spark.
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 928cc8e3559e13af66268f3d1b3766cf2df9041f
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223973"
---
# <a name="connect-net-for-apache-spark-to-mongodb"></a><span data-ttu-id="54d04-103">Conectar o .NET para Apache Spark ao MongoDB</span><span class="sxs-lookup"><span data-stu-id="54d04-103">Connect .NET for Apache Spark to MongoDB</span></span>

<span data-ttu-id="54d04-104">Neste artigo, você aprenderá a se conectar a uma instância do MongoDB de seu aplicativo .NET para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="54d04-104">In this article, you learn how to connect to a MongoDB instance from your .NET for Apache Spark application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54d04-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="54d04-105">Prerequisites</span></span>

1. <span data-ttu-id="54d04-106">Ter um servidor MongoDB em funcionamento com um [banco de dados e alguma coleção](https://docs.mongodb.com/manual/core/databases-and-collections/) adicionada a ele (Baixe [este servidor da Comunidade](https://www.mongodb.com/try/download/community) para um servidor local ou experimente o [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) para um serviço MongoDB na nuvem).</span><span class="sxs-lookup"><span data-stu-id="54d04-106">Have a MongoDB server up and running with a [database and some collection](https://docs.mongodb.com/manual/core/databases-and-collections/) added to it (Download [this community server](https://www.mongodb.com/try/download/community) for a local server or you can try [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) for a cloud MongoDB service.)</span></span>

## <a name="set-up-your-mongodb-instance"></a><span data-ttu-id="54d04-107">Configurar sua instância do MongoDB</span><span class="sxs-lookup"><span data-stu-id="54d04-107">Set up your MongoDB instance</span></span>

<span data-ttu-id="54d04-108">Para obter o .NET para Apache Spark se comunicar com sua instância do MongoDB, você precisa verificar se ele está configurado corretamente fazendo o seguinte:</span><span class="sxs-lookup"><span data-stu-id="54d04-108">In order to get .NET for Apache Spark to talk to your MongoDB instance you need to make sure it is set up correctly by doing the following:</span></span>

1. <span data-ttu-id="54d04-109">Crie um nome de usuário e uma senha para o seu aplicativo se conectar e forneça ao usuário as permissões/funções necessárias usando o seguinte comando por meio do Shell Mongo:</span><span class="sxs-lookup"><span data-stu-id="54d04-109">Create a username and password for your application to connect through, and give the user the necessary permissions/roles using the following command through mongo shell:</span></span>

    ```bash
    use database
    db.createUser(
      {
        user: "mySparkUser",
        pwd: "<password>",
        roles: [ { role: "userAdminAnyDatabase", db: "admin" }, "readWriteAnyDatabase" ]
      }
    )
    ```

2. <span data-ttu-id="54d04-110">Verifique se o endereço IP do computador no qual seu .NET para Apache Spark aplicativo está em execução está na lista de permissões para o servidor MongoDB ser capaz de se conectar.</span><span class="sxs-lookup"><span data-stu-id="54d04-110">Make sure the IP address of the machine your .NET for Apache Spark application is running on is whitelisted for the MongoDB server to be able to connect to.</span></span> <span data-ttu-id="54d04-111">Você pode consultar [este guia](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) para saber como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="54d04-111">You can refer to [this guide](https://docs.atlas.mongodb.com/security/add-ip-address-to-list/) to learn how to do that.</span></span>

## <a name="configure-your-net-for-apache-spark-application"></a><span data-ttu-id="54d04-112">Configurar seu .NET para Apache Spark aplicativo</span><span class="sxs-lookup"><span data-stu-id="54d04-112">Configure your .NET for Apache Spark application</span></span>

1. <span data-ttu-id="54d04-113">Tenha as seguintes variáveis definidas para configurar seu aplicativo para se comunicar com a instância do MongoDB e ler de uma coleção.</span><span class="sxs-lookup"><span data-stu-id="54d04-113">Have the following variables set to configure your application to talk to the MongoDB instance and read from a collection.</span></span>
    1. <span data-ttu-id="54d04-114">**authURI**: "cadeia de conexão que autoriza seu aplicativo a se conectar à instância necessária do MongoDB".</span><span class="sxs-lookup"><span data-stu-id="54d04-114">**authURI**: "Connection string authorizing your application to connect to the required MongoDB instance".</span></span> <span data-ttu-id="54d04-115">O formato para isso é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="54d04-115">The format for that is as follows:</span></span>

        ```
        "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>"
        ```

    2. <span data-ttu-id="54d04-116">**nome**de usuário: nome de usuário da conta que você criou na etapa 1 da seção anterior</span><span class="sxs-lookup"><span data-stu-id="54d04-116">**username**: Username of the account you created in Step 1 of the previous section</span></span>
    3. <span data-ttu-id="54d04-117">**senha**: senha da conta de usuário criada</span><span class="sxs-lookup"><span data-stu-id="54d04-117">**password**: Password of the user account created</span></span>
    4. <span data-ttu-id="54d04-118">**cluster_address**: nome de host/endereço do seu cluster MongoDB</span><span class="sxs-lookup"><span data-stu-id="54d04-118">**cluster_address**: hostname/address of your MongoDB cluster</span></span>
    5. <span data-ttu-id="54d04-119">**banco de dados**: o banco de dados MongoDB ao qual você deseja se conectar</span><span class="sxs-lookup"><span data-stu-id="54d04-119">**database**: The MongoDB database you want to connect to</span></span>
    6. <span data-ttu-id="54d04-120">**coleção**: a coleção do MongoDB que você deseja ler.</span><span class="sxs-lookup"><span data-stu-id="54d04-120">**collection**: The MongoDB collection you want to read.</span></span> <span data-ttu-id="54d04-121">(Para este exemplo, usamos o [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) arquivo de exemplo padrão fornecido com cada instalação do Apache Spark.)</span><span class="sxs-lookup"><span data-stu-id="54d04-121">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.)</span></span>

2. <span data-ttu-id="54d04-122">Use o `com.mongodb.spark.sql.DefaultSource` formato `spark.Read()` como mostrado abaixo em um trecho de código simples:</span><span class="sxs-lookup"><span data-stu-id="54d04-122">Use the `com.mongodb.spark.sql.DefaultSource` format is `spark.Read()` as shown below in a simple code snippet:</span></span>

    ```csharp
    class Program
    {
        static void Main()
        {
            var authURI = "mongodb+srv://<username>:<password>@<cluster_address>/<database>.<collection>?retryWrites=true&w=majority";
            SparkSession spark = SparkSession
                .Builder()
                .AppName("Connect to Mongo DB example")
                .Config("spark.mongodb.input.uri", authURI)
                .GetOrCreate();

            DataFrame df = spark.Read().Format("com.mongodb.spark.sql.DefaultSource").Load();
            df.PrintSchema();
            df.Show();
            spark.Stop();
        }
    }
    ```

## <a name="run-your-application"></a><span data-ttu-id="54d04-123">Executar seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="54d04-123">Run your application</span></span>

<span data-ttu-id="54d04-124">Para executar seu .NET para Apache Spark aplicativo, você deve definir o `mongo-spark-connector` módulo como parte da definição de compilação em seu projeto do Spark, usando o `libraryDependency` no `build.sbt` para projetos SBT.</span><span class="sxs-lookup"><span data-stu-id="54d04-124">In order to run your .NET for Apache Spark application, you should define the `mongo-spark-connector` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="54d04-125">Para ambientes Spark como `spark-submit` (ou `spark-shell` ), você deve usar a `--packages` opção de linha de comando da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="54d04-125">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-submit --master local --packages org.mongodb.spark:mongo-spark-connector_2.12:3.0.0 --class org.apache.spark.deploy.dotnet.DotnetRunner microsoft-spark-<version>.jar yourApp.exe
```

> [!NOTE]
> <span data-ttu-id="54d04-126">Certifique-se de incluir a versão do pacote de acordo com a versão do Spark em execução.</span><span class="sxs-lookup"><span data-stu-id="54d04-126">Make sure to include the package version in accordance with the version of Spark being run.</span></span>

<span data-ttu-id="54d04-127">O resultado, conforme exibido, é o dataframe ( `df` ), conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="54d04-127">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

```text
+--------------------+----+-------+
|                 _id| age|   name|
+--------------------+----+-------+
|[5f7c28438029a134...|null|Michael|
|[5f7c287f8029a134...|  30|   Andy|
|[5f7c289a8029a134...|  19| Justin|
+--------------------+----+-------+
```
