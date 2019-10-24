---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.
ms.date: 06/27/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 19efc8412d834d73069c61e1cc1ccd9e5eb8593b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72774369"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: introdução ao .NET para Apache Spark

Este tutorial ensina como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Prepare seu ambiente Windows para .NET para Apache Spark
> * Baixe o **Microsoft.Spark.Worker**
> * Compilar e executar um aplicativo .NET para Apache Spark simples

## <a name="prepare-your-environment"></a>Preparar seu ambiente

Antes de começar, verifique se você pode executar `dotnet`, `java`, `mvn`, `spark-shell` da linha de comando. Se seu ambiente já estiver preparado, você poderá pular para a próxima seção. Se você não puder executar um ou todos os comandos, siga as etapas abaixo.

1. Baixe e instale o [SDK do .NET Core 2.1x](https://dotnet.microsoft.com/download/dotnet-core/2.1). A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho. Use o comando `dotnet --version` do PowerShell para verificar a instalação.

2. Instale o [Visual Studio 2017](https://www.visualstudio.com/downloads/) ou o [Visual Studio 2019](https://visualstudio.microsoft.com/vs/preview/) com as atualizações mais recentes. Você pode usar Community, Professional ou Enterprise. A versão Community é gratuita.

   Escolha as seguintes cargas de trabalho durante a instalação:
      * Desenvolvimento de área de trabalho do .NET
          * Todos os componentes necessários
          * Ferramentas de desenvolvimento do .NET Framework 4.6.1
      * Desenvolvimento de plataforma cruzada do .NET Core
          * Todos os componentes necessários

3. Instale o [Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

    * Selecione a versão apropriada para seu sistema operacional. Por exemplo, selecione **jdk-8u201-windows-x64.exe** para um computador x64 do Windows.
    * Use o comando `java -version` do PowerShell para verificar a instalação.

4. Instale o [Apache Maven 3.6.0+](https://maven.apache.org/download.cgi).
    * Baixe o [Apache Maven 3.6.2](http://mirror.metrocast.net/apache/maven/maven-3/3.6.2/binaries/apache-maven-3.6.2-bin.zip).
    * Extraia para um diretório local. Por exemplo, `c:\bin\apache-maven-3.6.2\`.
    * Adicione o Apache Maven à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml). Se você tiver extraído para o `c:\bin\apache-maven-3.6.2\`, adicionará `c:\bin\apache-maven-3.6.2\bin` a seu PATH.
    * Use o comando `mvn -version` do PowerShell para verificar a instalação.

5. Instale o [Apache Spark 2.3 ou superior](https://spark.apache.org/downloads.html). Não há suporte para o Apache Spark 2.4 ou superior.
    * Baixe o [Apache Spark 2.3+](https://spark.apache.org/downloads.html) e extraia-o para uma pasta local usando uma ferramenta como [7-zip](https://www.7-zip.org/) ou [WinZip](https://www.winzip.com/). Por exemplo, você pode extraí-lo para `c:\bin\spark-2.3.2-bin-hadoop2.7\`.
    * Adicione o Apache Spark à sua [variável de ambiente PATH](https://www.java.com/en/download/help/path.xml). Se você tiver extraído para o `c:\bin\spark-2.3.2-bin-hadoop2.7\`, adicionará `c:\bin\spark-2.3.2-bin-hadoop2.7\bin` a seu PATH.
    * Adicione uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) chamada `SPARK_HOME`. Se você tiver extraído para `C:\bin\spark-2.3.2-bin-hadoop2.7\`, use `C:\bin\spark-2.3.2-bin-hadoop2.7\` para o **Valor da variável**.
    * Verifique se você pode executar `spark-shell` da linha de comando.

6. Configure o [WinUtils](https://github.com/steveloughran/winutils).
    * Baixe o binário **winutils.exe** do [repositório WinUtils](https://github.com/steveloughran/winutils). Selecione a versão do Hadoop com a qual a distribuição do Spark foi compilada. Por exemplo, você usa **hadoop-2.7.1** para **Spark 2.3.2**. A versão do Hadoop é anotada no final do nome da pasta de instalação do Spark.
    * Salve o binário **winutils.exe** em um diretório de sua escolha. Por exemplo, `c:\hadoop\bin`.
    * Defina `HADOOP_HOME` para refletir o diretório com **winutils.exe** sem `bin`. Por exemplo, `c:\hadoop`.
    * Defina a variável de ambiente PATH para incluir `%HADOOP_HOME%\bin`.

Verifique se você pode executar `dotnet`, `java`, `mvn`, `spark-shell` da linha de comando antes de passar para a próxima seção.

## <a name="download-the-microsoftsparkworker-release"></a>Baixe a versão Microsoft.Spark.Worker

1. Baixe a versão [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) da página Versões do GitHub do .NET para Apache Spark para seu computador local. Por exemplo, você pode baixá-lo para o caminho, `c:\bin\Microsoft.Spark.Worker\`.

2. Crie uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) chamada `DOTNET_WORKER_DIR` e defina-a para o diretório em que você baixou e extraiu **Microsoft.Spark.Worker**. Por exemplo, `c:\bin\Microsoft.Spark.Worker`.

## <a name="clone-the-net-for-apache-spark-github-repo"></a>Clonar o repositório do GitHub do .NET para Apache Spark

Use o comando [GitBash](https://gitforwindows.org/) a seguir para clonar o repositório do .NET para Apache Spark para seu computador.

```bash
git clone https://github.com/dotnet/spark.git c:\github\dotnet-spark
```

## <a name="write-a-net-for-apache-spark-app"></a>Escrever um aplicativo .NET para Apache Spark

1. Abra o **Visual Studio** e navegue até **Arquivo > Criar Projeto > Aplicativo de Console (.NET Core)** . Dê ao aplicativo o nome de **HelloSpark**.

2. Instale o [pacote NuGet do Microsoft.Spark](https://www.nuget.org/profiles/spark). Para obter mais informações sobre como instalar pacotes do NuGet, confira [Diferentes maneiras de instalar um pacote do NuGet](https://docs.microsoft.com/nuget/consume-packages/ways-to-install-a-package).

3. No **Gerenciador de Soluções**, abra **Program.cse** e escreva o código C# a seguir:

   ```csharp
     var spark = SparkSession.Builder().GetOrCreate();
     var df = spark.Read().Json("people.json");
     df.Show();
   ```

4. Compile a solução.

## <a name="run-your-net-for-apache-spark-app"></a>Executar seu aplicativo .NET para Apache Spark

1. Abra o **PowerShell** e altere o diretório para a pasta em que seu aplicativo está armazenado.

   ```powershell
   cd <your-app-output-directory>
   ```

2. Crie um arquivo chamado **people.json** com o seguinte conteúdo:

   ```json
   {"name":"Michael"}
   {"name":"Andy", "age":30}
   {"name":"Justin", "age":19}
   ```

3. Use o seguinte comando do PowerShell para executar seu aplicativo:

   ```powershell
    spark-submit `
    --class org.apache.spark.deploy.dotnet.DotnetRunner `
    --master local `
    microsoft-spark-2.4.x-<version>.jar `
    dotnet HelloSpark.dll
    ```

Parabéns! Você criou e executou com êxito um aplicativo .NET para Apache Spark.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
>
> * Prepare seu ambiente Windows para .NET para Apache Spark
> * Baixe o **Microsoft.Spark.Worker**
> * Compilar e executar um aplicativo .NET para Apache Spark simples

Confira a página de recursos para saber mais.
> [!div class="nextstepaction"]
> [Recursos do .NET para Apache Spark](../resources/index.md)
