---
title: Conectar-se ao armazenamento remoto do computador local
description: Conecte-se às contas de armazenamento do Azure usando .NET para Apache Spark do computador local.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 09e92b0cae848f9c98b691a11842f131f613396b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877827"
---
# <a name="connect-to-azure-data-lake-storage-gen-2-or-wasb-account"></a><span data-ttu-id="3a1a1-103">Conectar-se à conta do Azure Data Lake Storage Gen 2 ou WASB</span><span class="sxs-lookup"><span data-stu-id="3a1a1-103">Connect to Azure Data Lake Storage Gen 2 or WASB account</span></span>

<span data-ttu-id="3a1a1-104">Neste artigo, você aprende a se conectar a uma conta do Azure Data Lake Storage (ADLS) Gen 2 ou do Windows Azure Storage Blob (WASB) por meio de uma instância do [.net para Apache Spark](https://github.com/dotnet/spark) em execução localmente em seu computador Windows.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-104">In this article, you learn how to connect to an Azure Data Lake Storage (ADLS) Gen 2 or Windows Azure Storage Blob (WASB) account through an instance of [.NET for Apache Spark](https://github.com/dotnet/spark) running locally on your Windows machine.</span></span>

## <a name="set-up-the-environment"></a><span data-ttu-id="3a1a1-105">Configurar o ambiente</span><span class="sxs-lookup"><span data-stu-id="3a1a1-105">Set up the environment</span></span>

1. <span data-ttu-id="3a1a1-106">Baixe a distribuição Apache Spark compilada sem Hadoop do [site oficial](https://archive.apache.org/dist/spark/) (escolha uma versão [com suporte do .net para Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)) e extraia-a em um diretório.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-106">Download the Apache Spark distribution built without Hadoop from [official website](https://archive.apache.org/dist/spark/) (choose a version [supported by .NET for Apache Spark](https://github.com/dotnet/spark#supported-apache-spark)), and extract it to a directory.</span></span> <span data-ttu-id="3a1a1-107">Defina a variável de ambiente `SPARK_HOME` para esse diretório.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-107">Set the environment variable `SPARK_HOME` to this directory.</span></span>
2. <span data-ttu-id="3a1a1-108">Baixe o binário Apache Hadoop [aqui](http://hadoop.apache.org/releases.html) e extraia-o para uma pasta e defina a `HADOOP_HOME` variável de ambiente para essa pasta.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-108">Download the Apache Hadoop binary from [here](http://hadoop.apache.org/releases.html) and extract to a folder, and set your `HADOOP_HOME` environment variable to this folder.</span></span>
3. <span data-ttu-id="3a1a1-109">Baixe os `winutils.exe` `hadoop.dll` arquivos e deste [local](https://github.com/cdarlint/winutils) (dependendo da versão do Hadoop instalada na etapa anterior) e coloque-os na pasta bin do seu Hadoop.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-109">Download the `winutils.exe` and `hadoop.dll` files from [this location](https://github.com/cdarlint/winutils) (depending on the version of Hadoop installed in the previous step) and put them in the bin folder of your Hadoop.</span></span> <span data-ttu-id="3a1a1-110">Esses binários são necessários no Windows para que tudo seja configurado corretamente (isso é explicado em detalhes no [wiki do Apache aqui](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span><span class="sxs-lookup"><span data-stu-id="3a1a1-110">These binaries are needed on Windows in order to get everything setup correctly (this is explained in detail in the [Apache wiki here](https://cwiki.apache.org/confluence/display/HADOOP2/WindowsProblems)).</span></span>
4. <span data-ttu-id="3a1a1-111">Configure a instalação do Hadoop fazendo as seguintes alterações no `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` arquivo:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-111">Configure your Hadoop installation by making the following changes to your `%HADOOP_HOME%\etc\hadoop\hadoop-env.cmd` file:</span></span>
    1. <span data-ttu-id="3a1a1-112">Defina a `JAVA_HOME` propriedade usando o caminho dos (já que o Hadoop não gosta de espaços em `JAVA_HOME` ).</span><span class="sxs-lookup"><span data-stu-id="3a1a1-112">Set the `JAVA_HOME` property using the DOS path (since Hadoop doesn't like spaces in `JAVA_HOME`).</span></span> <span data-ttu-id="3a1a1-113">Isso deve ser semelhante a este: `C:\Progra~1\Java\jdk1.8.0_241` (apontando para qualquer versão do Java que você tenha instalado em seu computador local).</span><span class="sxs-lookup"><span data-stu-id="3a1a1-113">This should look something like this: `C:\Progra~1\Java\jdk1.8.0_241` (Pointing to whatever version of Java you have installed on your local machine).</span></span>
    2. <span data-ttu-id="3a1a1-114">Anexar `%HADOOP_HOME%\share\hadoop\tools\lib\*` a `HADOOP_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="3a1a1-114">Append `%HADOOP_HOME%\share\hadoop\tools\lib\*` to `HADOOP_CLASSPATH`.</span></span>
    <span data-ttu-id="3a1a1-115">O `hadoop-env.cmd` arquivo final deve ser semelhante a este:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-115">Your final `hadoop-env.cmd` file should look something like this:</span></span>

    ![Arquivo Hadoop-env. cmd final](./media/connect-external-sources/hadoop-env.png)

## <a name="configure-your-storage-account-in-hadoop"></a><span data-ttu-id="3a1a1-117">Configurar sua conta de armazenamento no Hadoop</span><span class="sxs-lookup"><span data-stu-id="3a1a1-117">Configure your storage account in Hadoop</span></span>

1. <span data-ttu-id="3a1a1-118">Abra a conta de armazenamento ADLS Gen 2 ou WASB à qual você deseja se conectar por meio da [portal do Azure](https://portal.azure.com) e abra o painel **chaves de acesso** na folha **configurações** e copie o valor da **chave** de em key1.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-118">Open the ADLS Gen 2 or WASB storage account you want to connect to through the [Azure portal](https://portal.azure.com) and open the **Access keys** panel under the **Settings** blade and copy the value of **Key** from under key1.</span></span>
2. <span data-ttu-id="3a1a1-119">Agora, para configurar o Hadoop para acessar sua conta de ADLS Gen2, você precisaria editar seu `core-site.xml` arquivo (localizado em `%HADOOP_HOME%\etc\hadoop\` ) que contém a configuração em todo o cluster.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-119">Now in order to configure Hadoop to access your ADLS Gen2 account you would have to edit your `core-site.xml` (located in `%HADOOP_HOME%\etc\hadoop\` ) file which contains cluster-wide configuration.</span></span> <span data-ttu-id="3a1a1-120">Adicione as seguintes propriedades dentro das `<configuration>` marcas neste arquivo:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-120">Add the following properties inside the `<configuration>` tags in this file:</span></span>

    ```xml
    <configuration>
      <property>
        <name>fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>SharedKey</value>
        <description></description>
      </property>
      <property>
        <name>fs.azure.account.key.YOUR_ACCOUNT_NAME.dfs.core.windows.net</name>
        <value>YOUR ACCESS KEY (copied from Step 1)</value>
        <description>The secret password. Never share these.</description>
      </property>
    </configuration>
    ```

    <span data-ttu-id="3a1a1-121">Se você estiver tentando se conectar a uma conta do WASB, substitua `dfs` por `blob` nos nomes de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-121">If you are trying to connect to a WASB account, replace `dfs` with `blob` in the property names.</span></span> <span data-ttu-id="3a1a1-122">Por exemplo, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-122">For example, `fs.azure.account.auth.type.YOUR_ACCOUNT_NAME.blob.core.windows.net`.</span></span>
3. <span data-ttu-id="3a1a1-123">Você pode testar a conectividade com sua conta de armazenamento do Hadoop executando o seguinte comando em seu `%HADOOP_HOME%` diretório:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-123">You can test the connectivity to your Storage Account from Hadoop by running the following command from your `%HADOOP_HOME%` directory:</span></span>

    ```bash
    bin\hdfs dfs -ls <URI to your account>
    ```

<span data-ttu-id="3a1a1-124">Isso deve exibir uma lista de todos os arquivos/pastas no caminho fornecido pelo URI.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-124">This should display a list of all files/folders in the path provided by your URI.</span></span>

> [!NOTE]
> <span data-ttu-id="3a1a1-125">O formato para derivar o URI para sua conta de armazenamento é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-125">The format to derive the URI to your Storage account is as follows:</span></span>
>
> ```
> For ADLS: abfs[s]://<file_system>@<account_name>.dfs.core.windows.net/<path>/<file_name>
> For WASB: wasb[s]://<file_system>@<account_name>.blob.core.windows.net/<path>/<file_name>
> ```

## <a name="connect-to-your-storage-account"></a><span data-ttu-id="3a1a1-126">Conectar-se à sua conta de armazenamento</span><span class="sxs-lookup"><span data-stu-id="3a1a1-126">Connect to your storage account</span></span>

1. <span data-ttu-id="3a1a1-127">Se o comando acima funcionou, agora você pode passar para acessar essa conta de armazenamento por meio do Spark.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-127">If the above command worked, you can now move on to accessing this storage account through Spark.</span></span> <span data-ttu-id="3a1a1-128">Primeiro, execute o comando a `hadoop classpath` partir da linha de comando dentro `%HADOOP_HOME%` e copie a saída.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-128">First run the command `hadoop classpath` from the commandline inside `%HADOOP_HOME%` and copy the output.</span></span>
2. <span data-ttu-id="3a1a1-129">Defina a saída do comando executado na etapa 1 para o valor da variável de ambiente `SPARK_DIST_CLASSPATH` .</span><span class="sxs-lookup"><span data-stu-id="3a1a1-129">Set the output of the command run in Step 1 to the value of environment variable `SPARK_DIST_CLASSPATH`.</span></span>
3. <span data-ttu-id="3a1a1-130">Agora você deve ser capaz de acessar sua conta de armazenamento do ADLS ou WASB por meio do Spark .NET usando o URI do abfs, conforme mostrado no exemplo simples abaixo.</span><span class="sxs-lookup"><span data-stu-id="3a1a1-130">Now you should be able to access your ADLS or WASB storage account through Spark .NET using the abfs URI as shown in the simple example below.</span></span> <span data-ttu-id="3a1a1-131">(Para este exemplo, usamos o [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) arquivo de exemplo padrão fornecido com cada instalação de Apache Spark.):</span><span class="sxs-lookup"><span data-stu-id="3a1a1-131">(For this example we use the standard [`people.json`](https://github.com/apache/spark/blob/master/examples/src/main/resources/people.json) example file provided with every Apache Spark installation.):</span></span>

    ```csharp
    SparkSession spark = SparkSession
       .Builder()
       .AppName("Connect to Azure Storage locally")
       .GetOrCreate();
    DataFrame df = spark.Read().Json("wasbs://file_system@account_name.blob.core.windows.net/path/people.json");
    //DataFrame df = spark.Read().Json("abfss://file_system@account_name.dfs.core.windows.net/path/file.json");
    df.Show();
    ```

    <span data-ttu-id="3a1a1-132">O resultado, conforme exibido, é o dataframe ( `df` ), conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="3a1a1-132">The result as displayed is the DataFrame (`df`) as shown below:</span></span>

    ```text
    +----+-------+
    | age|   name|
    +----+-------+
    |null|Michael|
    |  30|   Andy|
    |  19| Justin|
    +----+-------+
    ```
