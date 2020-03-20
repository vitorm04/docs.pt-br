---
title: Introdução ao .NET para Apache Spark
description: Descubra como executar um aplicativo .NET para Apache Spark usando .NET Core no Windows, MacOS e Ubuntu.
ms.date: 01/31/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7375c385245a05d7dc29d5df89d875bf6cb4141a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187538"
---
# <a name="tutorial-get-started-with-net-for-apache-spark"></a>Tutorial: Comece com .NET para Apache Spark

Este tutorial ensina como executar um aplicativo .NET para Apache Spark usando .NET Core no Windows, MacOS e Ubuntu.

Neste tutorial, você aprenderá como:

> [!div class="checklist"]
>
> * Prepare seu ambiente para .NET para Apache Spark
> * Escreva seu primeiro aplicativo .NET para Apache Spark
> * Construa e execute seu aplicativo .NET simples para Apache Spark

## <a name="prepare-your-environment"></a>Prepare o seu ambiente

Antes de começar a escrever seu aplicativo, você precisa configurar algumas dependências pré-requisitos. Se você `dotnet`pode `java` `mvn`executar `spark-shell` , , , a partir de seu ambiente de linha de comando, então o seu ambiente já está preparado e você pode pular para a próxima seção. Se você não puder executar qualquer ou todos os comandos, faça as seguintes etapas.

### <a name="1-install-net"></a>1. Instalar .NET

Para começar a criar aplicativos .NET, você precisa baixar e instalar o .NET SDK (Software Development Kit).

Baixe e instale o [SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/3.1). A instalação do SDK adiciona a cadeia de ferramentas `dotnet` a seu caminho.

Depois de instalar o .NET Core SDK, abra um novo `dotnet`prompt de comando ou terminal e execute .

Se o comando for executado e imprimir informações sobre como usar o dotnet, pode passar para o próximo passo. Se você `'dotnet' is not recognized as an internal or external command` receber um erro, certifique-se de abrir um **novo** prompt de comando ou terminal antes de executar o comando.

### <a name="2-install-java"></a>2. Instalar Java

Instale [java 8.1](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) para Windows e MacOS, ou [OpenJDK 8](https://openjdk.java.net/install/) para Ubuntu.

Selecione a versão apropriada para seu sistema operacional. Por exemplo, selecione **jdk-8u201-windows-x64.exe** para uma máquina Windows x64 (como mostrado abaixo) ou **jdk-8u231-macosx-x64.dmg** para MacOS. Em seguida, `java` use o comando para verificar a instalação.

![Java Download](https://dotnet.microsoft.com/static/images/java-jdk-downloads-windows.png?v=6BbJHoNyDO-PyYVciImr5wzh2AW_YHNcyb3p093AwPA)

### <a name="3-install-compression-software"></a>3. Instalar software de compressão

Apache Spark é baixado como um arquivo .tgz compactado. Use um programa de extração, como [7-Zip](https://www.7-zip.org/) ou [WinZip,](https://www.winzip.com/)para extrair o arquivo.

### <a name="4-install-apache-spark"></a>4. Instale a Faísca Apache

[Baixe e instale o Apache Spark](https://spark.apache.org/downloads.html). Você precisará selecionar entre as versões 2.3.* ou 2.4.0, 2.4.1, 2.4.3 ou 2.4.4 (.NET para Apache Spark não é compatível com outras versões do Apache Spark).

Os comandos usados nas etapas seguintes supõem que você [baixou e instalou o Apache Spark 2.4.1](https://archive.apache.org/dist/spark/spark-2.4.1/spark-2.4.1-bin-hadoop2.7.tgz). Se desejar usar uma versão diferente, substitua **o 2.4.1** pelo número de versão apropriado. Em seguida, extraia o arquivo **.tar** e os arquivos Apache Spark.

Para extrair o arquivo **aninhado .tar:**

* Localize o arquivo **spark-2.4.1-bin-hadoop2.7.tgz** que você baixou.
* Clique com o botão direito do mouse no arquivo e selecione **7-Zip-> Extrair aqui**.
* **spark-2.4.1-bin-hadoop2.7.tar** é criado ao lado do arquivo **.tgz** que você baixou.

Para extrair os arquivos apache spark:

* Clique com o botão direito do mouse em **spark-2.4.1-bin-hadoop2.7.tar** e selecione **arquivos 7-Zip-> Extract...**
* Digite **C:\bin** no **campo Extrair para.**
* Desmarcar a caixa de seleção abaixo **do campo Extrato para** campo.
* Selecione **OK**.
* Os arquivos Apache Spark são extraídos para C:\bin\spark-2.4.1-bin-hadoop2.7\

![Instalar Spark](https://dotnet.microsoft.com/static/images/spark-extract-with-7-zip.png?v=YvjUv54LIxI9FbALPC3h8zSQdyMtK2-NKbFOliG-f8M)

Execute os seguintes comandos para definir as variáveis de ambiente usadas para localizar o Apache Spark no **Windows**:

```console
setx HADOOP_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
setx SPARK_HOME C:\bin\spark-2.4.1-bin-hadoop2.7\
```

Execute os seguintes comandos para definir as variáveis de ambiente usadas para localizar o Apache Spark no **MacOS** e **no Ubuntu**:

```bash
export SPARK_HOME=~/bin/spark-2.4.1-bin-hadoop2.7/
export PATH="$SPARK_HOME/bin:$PATH"
source ~/.bashrc
```

Depois de instalar tudo e definir as variáveis do ambiente, abra um **novo** prompt de comando ou terminal e execute o seguinte comando:

`%SPARK_HOME%\bin\spark-submit --version`

Se o comando for executado e imprimir informações da versão, você pode passar para a próxima etapa.

Se você `'spark-submit' is not recognized as an internal or external command` receber um erro, certifique-se de abrir um **novo** prompt de comando.

### <a name="5-install-net-for-apache-spark"></a>5. Instale .NET para Apache Spark

Baixe a versão [Microsoft.Spark.Worker](https://github.com/dotnet/spark/releases) do .NET para Apache Spark GitHub. Por exemplo, se você estiver em uma máquina Windows e planeja usar o .NET Core, [baixe a versão netcoreapp3.1 do Windows x64](https://github.com/dotnet/spark/releases/download/v0.8.0/Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip).

Para extrair o Microsoft.Spark.Worker:

* Localize o arquivo **Microsoft.Spark.Worker.netcoreapp3.1.win-x64-0.8.0.zip** que você baixou.
* Clique com o botão direito do mouse e selecione **arquivos 7-Zip-> Extract...**.
* Digite **C:\bin** no **campo Extrair para.**
* Desmarcar a caixa de seleção abaixo **do campo Extrato para** campo.
* Selecione **OK**.

![Instale a faísca .NET](https://dotnet.microsoft.com/static/images/dotnet-for-spark-extract-with-7-zip.png?v=jwCyum9mL0mGIi4V5zC7yuvLfcj1_nL-QFFD8TClhZk)

### <a name="6-install-winutils-windows-only"></a>6. Instale o WinUtils (somente windows)

.NET para Apache Spark requer que o WinUtils seja instalado ao lado do Apache Spark. [Baixe winutils.exe](https://github.com/steveloughran/winutils/blob/master/hadoop-2.7.1/bin/winutils.exe). Em seguida, copie WinUtils em **C:\bin\spark-2.4.1-bin-hadoop2.7\bin**.

> [!NOTE]
> Se você estiver usando uma versão diferente do Hadoop, que é anotada no final do nome da pasta de instalação spark, [selecione a versão do WinUtils](https://github.com/steveloughran/winutils) compatível com a sua versão do Hadoop.

### <a name="7-set-dotnet_worker_dir-and-check-dependencies"></a>7. Defina DOTNET_WORKER_DIR e verifique dependências

Execute um dos seguintes comandos para definir a `DOTNET_WORKER_DIR` Variável de Ambiente, que é usada por aplicativos .NET para localizar .NET para Apache Spark.

No **Windows,** crie uma [nova variável](https://www.java.com/en/download/help/path.xml) `DOTNET_WORKER_DIR` de ambiente e defina-a no diretório onde você `C:\bin\Microsoft.Spark.Worker\`baixou e extraiu o Microsoft.Spark.Worker (por exemplo, ).

No **MacOS**, crie uma `export DOTNET_WORKER_DIR <your_path>` nova variável de ambiente usando e defina-a no diretório onde você baixou e extraiu o Microsoft.Spark.Worker (por exemplo, *~/bin/Microsoft.Spark.Worker/*).

No **Ubuntu,** crie uma [nova variável](https://help.ubuntu.com/community/EnvironmentVariables) `DOTNET_WORKER_DIR` de ambiente e defina-a no diretório onde você baixou e extraiu o Microsoft.Spark.Worker (por exemplo, *~/bin/Microsoft.Spark.Worker*).

Finalmente, verifique duas vezes `dotnet`se `java` `mvn`você `spark-shell` pode executar , , a partir de sua linha de comando antes de passar para a próxima seção.

## <a name="write-a-net-for-apache-spark-app"></a>Escrever um aplicativo .NET para Apache Spark

### <a name="1-create-a-console-app"></a>1. Crie um aplicativo de console

Em seu prompt de comando ou terminal, execute os seguintes comandos para criar um novo aplicativo de console:

```dotnetcli
dotnet new console -o mySparkApp
cd mySparkApp
```

O `dotnet` comando `new` cria uma `console` aplicação de tipo para você. O `-o` parâmetro cria um diretório chamado *mySparkApp* onde seu aplicativo é armazenado e o preenche com os arquivos necessários. O `cd mySparkApp` comando altera o diretório para o diretório de aplicativos que você acabou de criar.

### <a name="2-install-nuget-package"></a>2. Instale o pacote NuGet

Para usar o .NET para Apache Spark em um aplicativo, instale o pacote Microsoft.Spark. Em seu prompt de comando ou terminal, execute o seguinte comando:

`dotnet add package Microsoft.Spark --version 0.8.0`

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
            SparkSession spark = SparkSession
                .Builder()
                .AppName("word_count_sample")
                .GetOrCreate();

            // Create initial DataFrame.
            DataFrame dataFrame = spark.Read().Text("input.txt");

            // Count words.
            DataFrame words = dataFrame
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

### <a name="4-create-and-add-a-data-file"></a>4. Crie e adicione um arquivo de dados

Abra seu prompt de comando ou terminal e navegue na pasta do aplicativo.

```bash
cd <your-app-output-directory>
```

Seu aplicativo processa um arquivo contendo linhas de texto. Crie um arquivo *input.txt* no diretório *mySparkApp,* contendo o seguinte texto:

```text
Hello World
This .NET app uses .NET for Apache Spark
This .NET app counts words with Apache Spark
```

## <a name="run-your-net-for-apache-spark-app"></a>Executar seu aplicativo .NET para Apache Spark

1. Execute o seguinte comando para construir seu aplicativo:

   ```dotnetcli
   dotnet build
   ```

2. Execute o seguinte comando para enviar seu aplicativo para executar no Apache Spark:

   ```console
   spark-submit \
   --class org.apache.spark.deploy.dotnet.DotnetRunner \
   --master local \
   microsoft-spark-2.4.x-<version>.jar \
   dotnet HelloSpark.dll
   ```

   > [!NOTE]
   > Este comando pressupõe que você baixou o Apache Spark e `spark-submit`adicionou-o à sua variável de ambiente PATH para poder usar . Caso contrário, você teria que usar o caminho completo (por exemplo, *C:\bin\apache-spark\bin\bin\spark\spark-submit* ou *~/spark/bin/spark-submit*).

3. Quando o aplicativo é executado, os dados de contagem de palavras do arquivo *input.txt* são gravados no console.

Parabéns! Você criou e executou com êxito um aplicativo .NET para Apache Spark.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você aprendeu a:
> [!div class="checklist"]
>
> * Prepare seu ambiente Windows para .NET para Apache Spark
> * Escreva seu primeiro aplicativo .NET para Apache Spark
> * Construa e execute seu aplicativo .NET simples para Apache Spark

Para ver um vídeo explicando os passos acima, confira a [série de vídeos .NET para Apache Spark 101](https://channel9.msdn.com/Series/NET-for-Apache-Spark-101/Run-Your-First-NET-for-Apache-Spark-App).

Confira a página de recursos para saber mais.
> [!div class="nextstepaction"]
> [Recursos do .NET para Apache Spark](../resources/index.md)
