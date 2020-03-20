---
title: Envie um trabalho .NET para Apache Spark para Databricks
description: Saiba como enviar um trabalho .NET para Apache Spark para Databricks usando spark-submit e Set Jar.
ms.date: 12/05/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 65976f9095ecef66e0538c398492033c612c1430
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187602"
---
# <a name="submit-a-net-for-apache-spark-job-to-databricks"></a>Envie um trabalho .NET para Apache Spark para Databricks

Existem duas maneiras de implantar seu trabalho .NET `spark-submit` para Apache Spark no Databricks: e Definir Jar.

## <a name="deploy-using-spark-submit"></a>Implantar usando o envio de faíscas

Você pode usar o comando [spark-submit](https://spark.apache.org/docs/latest/submitting-applications.html) para enviar .NET para trabalhos do Apache Spark para Databricks. `spark-submit`permite a submissão apenas a um cluster que é criado demanda.

1. Navegue até o seu Databricks Workspace e crie um trabalho. Escolha um título para o seu trabalho e, em seguida, selecione **Configurar envio de faíscas**. Cole os seguintes parâmetros na configuração do trabalho e **selecione Confirmar**.

    ```
    ["--files","/dbfs/<path-to>/<app assembly/file to deploy to worker>","--class","org.apache.spark.deploy.dotnet.DotnetRunner","/dbfs/<path-to>/microsoft-spark-<spark_majorversion.spark_minorversion.x>-<spark_dotnet_version>.jar","/dbfs/<path-to>/<app name>.zip","<app bin name>","app arg1","app arg2"]
    ```

    > [!NOTE]
    > Atualize o conteúdo do parâmetro acima com base em seus arquivos e configuração específicos. Por exemplo, faça referência à versão do arquivo de jaro Microsoft.Spark que você carregou para o DBFS e use o nome apropriado do seu aplicativo e publicado arquivo zip do aplicativo.

2. Navegue até o seu trabalho e selecione **Editar** para configurar o cluster do seu trabalho. Defina a versão de tempo de execução de databricks com base na versão do Apache Spark que deseja usar em sua implantação. Em seguida, selecione **Opções Avançadas > Scripts Init**e defina Init Script Path como `dbfs:/spark-dotnet/db-init.sh`. Selecione **Confirmar** para confirmar as configurações do cluster.

3. Navegue até o seu trabalho e selecione **Executar agora** para executar seu trabalho no cluster Spark recém-configurado. Leva alguns minutos para o cluster do trabalho ser criado. Uma vez criado, seu trabalho será submetido. Você pode exibir a saída selecionando **Clusters** no menu esquerdo do espaço de trabalho databricks e, em seguida, selecione **Registros de driver**.

## <a name="deploy-using-set-jar"></a>Implantar usando set jar

Alternativamente, você pode usar [Set Jar](https://docs.microsoft.com/azure/databricks/jobs#--create-a-job) em seu espaço de trabalho Databricks para enviar .NET para trabalhos Apache Spark para Databricks. *Set Jar* permite a submissão de trabalho a um cluster ativo existente.

### <a name="one-time-setup"></a>Configuração única

1. Navegue até o cluster Databricks e selecione **Trabalhos** no menu do lado esquerdo, seguido por **Set JAR**.

2. Faça o `microsoft-spark-<spark-version>-<spark-dotnet-version>.jar`upload do apropriado .

3. Modifique os seguintes parâmetros para incluir o nome `<your-app-name>`correto para o executável que você publicou no lugar de :

    ```
    Main Class: org.apache.spark.deploy.dotnet.DotnetRunner
    Arguments /dbfs/apps/<your-app-name>.zip <your-app-name>
    ```

4. Configure o cluster para apontar para um cluster existente para o qual você já definiu o script init.

### <a name="publish-and-run-your-app"></a>Publicar e executar seu aplicativo

1. Certifique-se de que você publicou seu aplicativo `SparkSession.Stop()`e que seu código de aplicativo não use .

2. Use [o Databricks CLI](https://docs.microsoft.com/azure/databricks/dev-tools/databricks-cli) para carregar seu aplicativo no cluster Databricks. Por exemplo, use o seguinte comando para carregar seu aplicativo publicado no cluster:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <your-app-name>.zip dbfs:/apps/<your-app-name>.zip
    ```

3. Se você tiver alguma função definida pelo usuário em seu aplicativo, os conjuntos de aplicativos, como DLLs que contêm funções definidas pelo usuário, juntamente com suas dependências, precisam ser colocados no diretório de trabalho de cada *Microsoft.Spark.Worker*.

    Carregue seus conjuntos de aplicativos para o cluster Databricks:

    ```console
    cd <path-to-your-app-publish-directory>
    databricks fs cp <assembly>.dll dbfs:/apps/dependencies
    ```

    Descomentar e modificar a seção dependências do aplicativo em [db-init.sh](https://github.com/dotnet/spark/blob/master/deployment/db-init.sh) apontar para o caminho das dependências do aplicativo. Em seguida, carregue o *db-init.sh* atualizado para o seu cluster:

    ```console
    cd <path-to-db-init-and-install-worker>
    databricks fs cp db-init.sh dbfs:/spark-dotnet/db-init.sh
    ```

4. Navegue até **o cluster Databricks > Jobs > [Nome do trabalho] > Execute agora** para executar seu trabalho.

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao .NET para Apache Spark](../tutorials/get-started.md)
* [Implantar um aplicativo .NET para Apache Spark no Databricks](../tutorials/databricks-deployment.md)
* [Documentação do Azure Databricks](https://docs.microsoft.com/azure/azure-databricks/)
