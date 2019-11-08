---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.
ms.date: 11/04/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 1b736e078eea40e399882c0df020062b6aa758ad
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740519"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: introdução ao .NET para Apache Spark

Este tutorial ensina como executar um aplicativo .NET para Apache Spark usando o .NET Core no Windows.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Prepare seu ambiente Windows para .NET para Apache Spark
> * Escreva seu primeiro .NET para Apache Spark aplicativo
> * Crie e execute seu aplicativo .NET simples para Apache Spark

## <a name="prepare-your-environment"></a>Preparar seu ambiente

Antes de começar a escrever seu aplicativo, você precisa configurar algumas dependências de pré-requisito. Se você puder executar `dotnet`, `java`, `mvn``spark-shell` de seu ambiente de linha de comando, seu ambiente já estará preparado e você poderá pular para a próxima seção. Se você não puder executar um ou todos os comandos, execute as etapas a seguir.

### <a name="1-install-net"></a>1. instalar o .NET

Para começar a criar aplicativos .NET, você precisa baixar e instalar o SDK do .NET (Software Development Kit).

faça download e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.0). A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho. 

Depois de instalar o SDK do .NET Core, abra um novo prompt de comando e execute `dotnet`.

Se o comando executar e imprimir as informações sobre como usar dotnet, o poderá passar para a próxima etapa. Se você receber um erro de `'dotnet' is not recognized as an internal or external command`, certifique-se de ter aberto um **novo** prompt de comando antes de executar o comando. 

### <a name="2-install-java"></a>2. instalar o Java

Instale o [Java 8,1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

Selecione a versão apropriada para seu sistema operacional. Por exemplo, selecione **jdk-8u201-windows-x64.exe** para um computador x64 do Windows. Em seguida, use o comando `java` para verificar a instalação.
   
![Download do Java](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-7-zip"></a>3. instalar o 7-zip

Apache Spark é baixado como um arquivo. tgz compactado. Use um programa de extração, como 7-zip, para extrair o arquivo.

* Visite [7-Downloads de zip](https://www.7-zip.org/).
* Na primeira tabela da página, selecione o download do x86 de 32 bits ou de 64 bits x64, dependendo do seu sistema operacional.
* Quando o download for concluído, execute o instalador.
   
![Download do 7Zip](https://dotnet.microsoft.com/static/images/7-zip-downloads.png?v=W6qWtFC1tTMKv3YGXz7lBa9F3M22uWyTvkMmunyroNk)

### <a name="4-install-apache-spark"></a>4. instalar o Apache Spark

[Baixe e instale o Apache Spark](https://spark.apache.org/downloads.html). Você precisará selecionar a partir da versão 2,3. * ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET para Apache Spark não é compatível com outras versões do Apache Spark).  

Os comandos usados nas etapas a seguir pressupõem que você tenha [baixado e instalado Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Se você quiser usar uma versão diferente, substitua **2.4.1** pelo número de versão apropriado. Em seguida, extraia o arquivo **. tar** e os arquivos de Apache Spark.

Para extrair o arquivo **. tar** aninhado:

* Localize o arquivo **Spark-2.4.1-bin-Hadoop 2.7. tgz** que você baixou.
* Clique com o botão direito do mouse no arquivo e selecione **7-zip-> extrair aqui**.
* **Spark-2.4.1-bin-Hadoop 2.7. tar** é criado junto com o arquivo **. tgz** que você baixou.

Para extrair os arquivos de Apache Spark:

* Clique com o botão direito do mouse em **Spark-2.4.1-bin-Hadoop 2.7. tar** e selecione **7-zip-> extrair arquivos...**
* Insira **C:\bin** no campo **extrair para** .
* Desmarque a caixa de seleção abaixo do campo **extrair para** .
* Selecione **OK**.
* Os arquivos de Apache Spark são extraídos para C:\bin\spark-2.4.1-bin-hadoop2.7\
      
![Instalar o Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)
    
Execute os seguintes comandos para definir as variáveis de ambiente usadas para localizar Apache Spark:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Depois de instalar tudo e definir suas variáveis de ambiente, abra um **novo** prompt de comando e execute o seguinte comando:

`%SPARK_HOME%\bin\spark-submit --version`

Se o comando executar e imprimir as informações de versão, você poderá passar para a próxima etapa.

Se você receber um erro de `'spark-submit' is not recognized as an internal or external command`, certifique-se de ter aberto um **novo** prompt de comando.

### <a name="5-install-net-for-apache-spark"></a>5. instalar o .NET para Apache Spark

Baixe a versão [Microsoft. Spark. Worker](https://github.com/dotnet/spark/releases) do .net para Apache Spark github. Por exemplo, se você estiver em um computador Windows e planeja usar o .NET Core, [Baixe a versão Windows x64 netcoreapp 2.1](https://github.com/dotnet/spark/releases/download/v0.5.0/Microsoft.Spark.Worker.netcoreapp2.1.win-x64-0.6.0.zip).

Para extrair o Microsoft. Spark. Worker:

* Localize o arquivo **Microsoft. Spark. Worker. netcoreapp 2.1. Win-x64-0.6.0. zip** que você baixou.
* Clique com o botão direito do mouse e selecione **7-zip-> extrair arquivos...** .
* Insira **C:\bin** no campo **extrair para** .
* Desmarque a caixa de seleção abaixo do campo **extrair para** .
* Selecione **OK**.
  
![Instalar o .NET Spark](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils"></a>6. instalar o WinUtils

O .NET para Apache Spark requer que o WinUtils seja instalado junto com Apache Spark. [Baixe o winutils. exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Em seguida, copie WinUtils para **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Se você estiver usando uma versão diferente do Hadoop, que é anotada no final do nome da pasta de instalação do Spark, [Selecione a versão do WinUtils](https://github.com/steveloughran/winutils) que é compatível com sua versão do Hadoop. 

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. definir DOTNET_WORKER_DIR e verificar dependências

Execute o comando a seguir para definir a variável de ambiente `DOTNET_WORKER_DIR`, que é usada pelos aplicativos .NET para localizar o .NET para Apache Spark:

`setx DOTNET_WORKER_DIR "C:\bin\Microsoft.Spark.Worker-0.6.0"`

Por fim, verifique se você pode executar `dotnet`, `java`, `mvn``spark-shell` da linha de comando antes de passar para a próxima seção.

## <a name="write-a-net-for-apache-spark-app"></a>Escrever um aplicativo .NET para Apache Spark

### <a name="1-create-a-console-app"></a>1. criar um aplicativo de console

No prompt de comando, execute os seguintes comandos para criar um novo aplicativo de console:

```console
dotnet new console -o mySparkApp
cd mySparkApp
```

O comando `dotnet` cria um aplicativo `new` do tipo `console` para você. O parâmetro `-o` cria um diretório chamado *mySparkApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários. O comando `cd mySparkApp` altera o diretório para o diretório de aplicativo que você acabou de criar.

### <a name="2-install-nuget-package"></a>2. instalar o pacote NuGet

Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft. Spark. No prompt de comando, execute o seguinte comando:

`dotnet add package Microsoft.Spark --version 0.6.0`

### <a name="3-code-your-app"></a>3. Codifique seu aplicativo

Abra *Program.cs* no Visual Studio Code, ou em qualquer editor de texto, e substitua todo o código pelo seguinte:

```csharp
using Microsoft.Spark.Sql;

namespace MySparkApp
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a Spark session.
            var spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            var words = dataFrame
                .Select(Functions.Split(Functions.Col("value"), " ").Alias("words"))
                .Select(Functions.Explode(Functions.Col("words"))
                .Alias("word"))
                .GroupBy("word")
                .Count()
                .OrderBy(Functions.Col("count").Desc());

            // Show results.
            words.Show();

            // Stop Spark session.
            spark.Stop();
        }
    }
}
```

### <a name="4-add-data-file"></a>4. Adicionar arquivo de dados

Seu aplicativo processa um arquivo que contém linhas de texto. Crie um arquivo *Input. txt* no diretório *mySparkApp* , contendo o seguinte texto:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Executar seu aplicativo .NET para Apache Spark

1. Execute o seguinte comando para compilar seu aplicativo:

   ```dotnetcli
   dotnet build
   ```

2. Execute o seguinte comando para enviar seu aplicativo para execução no Apache Spark:

   ```powershell
   %SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local bin\Debug\netcoreapp3.0\microsoft-spark-2.4.x-0.6.0.jar dotnet bin\Debug\netcoreapp3.0\mySparkApp.dll
   ```

3. Quando seu aplicativo é executado, os dados de contagem de palavras do arquivo *Input. txt* são gravados no console do.

Parabéns! Você criou e executou com êxito um aplicativo .NET para Apache Spark.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu como:
> [!div class="checklist"]
>
> * Prepare seu ambiente Windows para .NET para Apache Spark
> * Escreva seu primeiro .NET para Apache Spark aplicativo
> * Crie e execute seu aplicativo .NET simples para Apache Spark

Para ver um vídeo explicando as etapas acima, faça checkout da [série de vídeos .net para Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Confira a página de recursos para saber mais.
> [!div class="nextstepaction"]
> [Recursos do .NET para Apache Spark](../resources/index.md)
