---
title: Implantar .NET para o trabalhador Apache Spark e binários de função definidos pelo usuário
description: Saiba como implantar o .NET para o trabalhador Apache Spark e binários de função definidos pelo usuário.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187589"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Implantar .NET para o trabalhador Apache Spark e binários de função definidos pelo usuário

Este como fornecer instruções gerais sobre como implantar .NET para o trabalhador Apache Spark e binários de função definidos pelo usuário. Você aprende quais variáveis de ambiente configurar, bem como alguns parâmetros comumente usados para lançar aplicativos com `spark-submit`.

## <a name="configurations"></a>Configurações
As configurações mostram as variáveis e configurações de parâmetros do ambiente geral para implantar o .NET para o trabalhador Apache Spark e binários de função definidos pelo usuário.

### <a name="environment-variables"></a>Variáveis de ambiente
Ao implantar trabalhadores e escrever UDFs, existem algumas variáveis de ambiente comumente usadas que você pode precisar definir:

| Variável de ambiente         | Descrição
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Caminho onde <code>Microsoft.Spark.Worker</code> o binário foi gerado.</br>É usado pelo motorista da Spark e será passado para os executores da Spark. Se essa variável não estiver configurada, os executores do <code>PATH</code> Spark procurarão o caminho especificado na variável ambiente.</br>_por exemplo, "C:\bin\Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Caminhos separados por <code>Microsoft.Spark.Worker</code> comma onde carregarão montagens.</br>Observe que se um caminho começar com ".", o diretório de trabalho será preparado. Se no **modo fio**, "." representaria o diretório de trabalho do contêiner.</br>_por\\&lt;exemplo, "C:\Users&gt;\\&lt;user name&gt;mysparkapp\\&lt;\bin\Debug dotnet version"&gt;_
| DOTNET_WORKER_DEBUG          | Se você quiser <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">depurar um UDF,</a> <code>1</code> defina <code>spark-submit</code>essa variável de ambiente para antes de ser executado .

### <a name="parameter-options"></a>Opções de parâmetro
Uma vez que o aplicativo Spark é `spark-submit` [empacotado,](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)você pode lançá-lo usando . A tabela a seguir mostra algumas das opções comumente utilizadas:

| Nome do Parâmetro        | Descrição
| :---------------------| :----------
| --classe               | O ponto de entrada para sua aplicação.</br>_por exemplo, org.apache.spark.deploy.dotnet.DotnetRunner_
| --mestre              | A <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">URL mestre</a> para o cluster.</br>_por exemplo, fios_
| --modo de implantação         | Seja para implantar seu driver nos<code>cluster</code>nós do trabalhador ( )<code>client</code>ou localmente como um cliente externo ( ).</br>Padrão: <code>client</code>
| --conf                | Propriedade de configuração <code>key=value</code> de Faísca Arbitrária em formato.</br>_por exemplo, spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=.\worker\Microsoft.Spark.Worker_
| --arquivos               | Lista separada por comma de arquivos a serem colocados no diretório de trabalho de cada executor.<br/><ul><li>Por favor, note que esta opção só é aplicável para o modo fio.</li><li>Ele suporta especificar nomes de arquivos com # semelhante a Hadoop.</br></ul>_por <code>myLocalSparkApp.dll#appSeen.dll</code>exemplo. Seu aplicativo deve usar <code>appSeen.dll</code> o <code>myLocalSparkApp.dll</code> nome como referência ao executar no YARN._</li>
| --arquivos          | Lista separada por comma de arquivos a serem extraídos no diretório de trabalho de cada executor.</br><ul><li>Por favor, note que esta opção só é aplicável para o modo fio.</li><li>Ele suporta especificar nomes de arquivos com # semelhante a Hadoop.</br></ul>_por <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>exemplo. Isso irá copiar e extrair <code>worker</code> o arquivo zip para pasta._</li>
| pote de aplicação       | Caminho para um frasco empacotado, incluindo sua aplicação e todas as dependências.</br>_por exemplo,&lt;hdfs:// caminho&gt;para o seu&lt;&gt;jar /microsoft-spark-versão .jar_
| argumentos de aplicação | Os argumentos passaram para o método principal da sua classe principal, se houver.</br>_por exemplo,&lt;hdfs:// caminho&gt;/&lt;para&gt;o &lt;seu aplicativo&gt; &lt;seu aplicativo .zip seu nome de aplicativo app args&gt;_

> [!NOTE]
> Especifique todos os `--options` antes `application-jar` ao iniciar aplicativos com , caso `spark-submit`contrário, eles serão ignorados. Para obter mais informações, consulte [ `spark-submit` opções](https://spark.apache.org/docs/latest/submitting-applications.html) e [a centelha em execução nos detalhes do YARN](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Quando executo um aplicativo de faísca com UDFs, recebo um erro 'FileNotFoundException'. O que devo fazer?
> **Erro:** [Erro] [TaskRunner] [TaskRunner] [0] ProcessStream() falhou com exceção: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null' arquivo não encontrado: 'mySparkApp.dll'

**Resposta:** Verifique se `DOTNET_ASSEMBLY_SEARCH_PATHS` a variável ambiente está definida corretamente. Deve ser o caminho `mySparkApp.dll`que contém o seu.

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Depois que atualizei minha versão .NET `DOTNET_WORKER_DIR` para Apache Spark e redefini `IOException` a variável de ambiente, por que ainda recebo o seguinte erro?
> **Erro:** Tarefa perdida 0.0 no estágio 11.0 (TID 24, localhost, executor driver): java.io.IOException: Não é possível executar o programa "Microsoft.Spark.Worker.exe": CreateProcess error=2, O sistema não consegue encontrar o arquivo especificado.

**Resposta:** Tente reiniciar sua janela PowerShell (ou outras janelas de comando) primeiro para que ele possa pegar os valores mais recentes da variável ambiente. Então comece seu programa.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Depois de enviar meu aplicativo Spark, eu recebo o erro `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.
> **Erro:** [Erro] [TaskRunner] [TaskRunner] [0] ProcessStream() falhou com exceção: System.TypeLoadException: Não foi possível carregar o tipo 'System.Runtime.Remoting.Contexts.Contexts', do conjunto 'mscorlib, Version=4.0.0.0, Culture=neutral, PublicKeyToken=...'.

**Resposta:** Verifique `Microsoft.Spark.Worker` a versão que você está usando. Existem duas versões: **.NET Framework 4.6.1** e **.NET Core 2.1.x**. Neste caso, `Microsoft.Spark.Worker.net461.win-x64-<version>` (que você pode [baixar](https://github.com/dotnet/spark/releases) `System.Runtime.Remoting.Contexts.Context` ) deve ser usado, pois é apenas para .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Como executar meu aplicativo de faísca com UDFs no YARN? Quais variáveis de ambiente e parâmetros devo usar?

**Resposta:** Para iniciar o aplicativo de faísca no YARN, `spark.yarn.appMasterEnv.[EnvironmentVariableName]`as variáveis de ambiente devem ser especificadas como . Veja abaixo como um `spark-submit`exemplo usando:

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Próximas etapas

* [Introdução ao .NET para Apache Spark](../tutorials/get-started.md)
* [Depurar um aplicativo .NET para Apache Spark no Windows](../how-to-guides/debug.md)
