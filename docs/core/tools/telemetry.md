---
title: Telemetria de Ferramentas da CLI do .NET Core
description: "Descubra os recursos de telemetria das ferramentas do .NET Core que coletam informações de uso para análise, quais dados são coletados e como desabilitá-la."
keywords: .NET,.NET Core,telemetria
author: richlander
ms.author: mairaw
ms.date: 08/04/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.openlocfilehash: 34183792a235391f66fbec211ff00f06f85134fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="net-core-cli-tools-telemetry"></a>Telemetria de Ferramentas da CLI do .NET Core

O [SDK do .NET Core](index.md) inclui um [recurso de telemetria](https://github.com/dotnet/cli/pull/2145) que coleta informações de uso. É importante que a Equipe do .NET compreenda como as ferramentas são usadas para que possamos melhorá-las. Para obter mais informações, consulte [What we've learned from .NET Core SDK Telemetry](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/) (O que aprendemos com a telemetria do SDK do .NET Core).

Os dados coletados são anônimos e são publicados de forma agregada para serem usados pela Microsoft e pela comunidade sob a [Licença de Atribuição Creative Commons](https://creativecommons.org/licenses/by/4.0/). 

## <a name="scope"></a>Escopo

O comando `dotnet` é usado para inicializar os aplicativos e a CLI do .NET Core. O comando `dotnet` em si não realiza coletas de telemetria. Os comandos da CLI do .NET Core são executados pelo comando `dotnet` para realizar coletas de telemetria.

A telemetria *não é habilitada* ao usar o comando `dotnet` em si sem nenhum comando anexado:

- `dotnet`
- `dotnet [path-to-app]`

A telemetria *é habilitada* ao usar os [comandos da CLI do .NET Core](index.md), como:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`


## <a name="behavior"></a>Comportamento

O recurso de telemetria das Ferramentas da CLI do .NET Core é habilitado por padrão. Recuse o recurso de telemetria definindo a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.

## <a name="data-points"></a>Pontos de dados

O recurso coleta os seguintes dados:

- Carimbo de data/hora da invocação&#8224;
- Comando invocado (por exemplo, "build")&#8224;
- Três endereços IP octet usados para determinar a localização geográfica&#8224;
- `ExitCode` do comando
- Executor de teste (para projetos de teste)
- Sistema operacional e versão&#8224;
- Se as IDs de tempo de execução estão presentes no nó de tempos de execução
- Versão do SDK do .NET Core&#8224;

&#8224;Essa métrica é publicada.

A partir do SDK 2.0 do .NET Core, os novos pontos de dados são coletados:

- opções e argumentos de comando do `dotnet`: somente argumentos e opções conhecidos são coletados (não cadeias de caracteres arbitrárias).
- Se o SDK está em execução em um contêiner.
- Estruturas de destino.
- Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador. Essa métrica não é publicada.
- Diretório de trabalho atual com hash.

O recurso não coleta dados pessoais como nomes de usuário ou endereços de emails. Ele não examina seu código e não extrai dados de nível de projeto confidenciais, como nome, repositório ou autor. Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e publicados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.

Desejamos saber como as ferramentas são usadas e se elas estão funcionando bem, não o que você está compilando com elas. Se você suspeitar que a telemetria está coletando dados confidenciais ou que nós estamos tratando dados de maneira insegura ou inadequada, [registre um problema nos problemas do repositório dotnet/cli](https://github.com/dotnet/cli/issues) para investigação.

## <a name="published-data"></a>Dados publicados

Os dados publicados estão disponíveis trimestralmente e são listados em [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Dados de uso do SDK do .NET Core). As colunas de um arquivo de dados são:
- Timestamp
- Ocorrências&#8224;
- Comando
- Geografia&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;A coluna *Ocorrências* exibe uma contagem agregada do uso desse comando para as métricas dessa linha naquele dia. 

&#8225;Normalmente, a coluna *Geografia* exibe o nome de um país. Em alguns casos, continente da Antártida aparece na coluna, devido ao fato de os pesquisadores usarem o .NET Core na Antártida ou a dados de localização incorretos.

### <a name="example"></a>Exemplo

| Timestamp      | Ocorrências | Comando | Geografia | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | executar     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Conjuntos de dados

[2016 – T3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)  
[2016 – T4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)  
[2017 – T1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)  
[2017 – T2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)

Outros conjuntos de dados são publicados usando um formato de URL padrão. Substitua `<YEAR>` pelo ano e substitua `<QUARTER>` pelo trimestre do ano (use `1`, `2`, `3` ou `4`). Os arquivos estão no formato *TSV* (valores separados por tabulação). 

```
https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv
```

## <a name="license"></a>Licença

A distribuição da Microsoft do .NET Core é licenciada com o [EULA da MICROSOFT .NET LIBRARY](https://aka.ms/dotnet-core-eula). Esta licença inclui a seção “DADOS” para habilitar a telemetria (mostrada abaixo).

Os [Pacotes NuGet do .NET](https://www.nuget.org/profiles/dotnetframework) usam essa mesma licença, mas não habilitam a telemetria (consulte o [Escopo](#scope)).

> 2. DADOS. O software pode coletar informações sobre você e seu uso do software e enviá-las para a Microsoft. A Microsoft pode usar essas informações para melhorar nossos produtos e serviços. Você pode saber mais sobre coleta e uso de dados na Documentação de Ajuda e na política de privacidade em http://go.microsoft.com/fwlink/?LinkId=528096. O uso do software serve como consentimento para essas práticas.

## <a name="disclosure"></a>Divulgação

As Ferramentas da CLI do .NET Core exibem o texto a seguir quando você executa um dos comandos pela primeira vez (por exemplo, `dotnet restore`). O texto pode variar um pouco dependendo da versão do SDK que você está executando. Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.
 
Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience. The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.
```

## <a name="see-also"></a>Consulte também

[O que aprendemos com a telemetria do SDK do .NET Core](https://blogs.msdn.microsoft.com/dotnet/2017/07/21/what-weve-learned-from-net-core-sdk-telemetry/)  
[Fonte de referência de telemetria (repositório dotnet/da cli; versão/branch 2.0.0)](https://github.com/dotnet/cli/blob/release/2.0.0/src/dotnet/Telemetry.cs)   
[Dados de uso do SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
