---
title: Telemetria do SDK do .NET Core
description: Descubra os recursos de telemetria do SDK do .NET Core que coletam informações de uso para análise, quais dados são coletados e como desabilitá-los.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 85cceab08fc6e4108a5b951c8b67c1ad5a28f6bb
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377497"
---
# <a name="net-core-sdk-telemetry"></a>Telemetria do SDK do .NET Core

O [SDK do .NET Core](index.md) inclui um [recurso de telemetria](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) que coleta informações de uso. É importante que a Equipe do .NET entenda como as ferramentas são usadas para que possa melhorá-las. Para obter mais informações, consulte [What we've learned from .NET Core SDK Telemetry](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/) (O que aprendemos com a telemetria do SDK do .NET Core).

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

## <a name="how-to-opt-out"></a>Como recusar

O recurso de telemetria do SDK do .NET Core é habilitado por padrão. Recuse o recurso de telemetria configurando a variável de ambiente `DOTNET_CLI_TELEMETRY_OPTOUT` como `1` ou `true`.

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

A partir do SDK do .NET Core 2.0, novos pontos de dados são coletados:

- opções e argumentos de comando do `dotnet`: somente argumentos e opções conhecidos são coletados (não cadeias de caracteres arbitrárias).
- Se o SDK está em execução em um contêiner.
- Estruturas de destino.
- Endereço MAC com hash: uma ID única e criptograficamente anônima (SHA256) para um computador. Essa métrica não é publicada.
- Diretório de trabalho atual com hash.

O recurso não coleta dados pessoais como nomes de usuário ou endereços de emails. Ele não examina seu código e não extrai dados de nível de projeto confidenciais, como nome, repositório ou autor. Os dados são enviados com segurança para os servidores Microsoft usando a tecnologia [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), mantidos em acesso restrito e publicados sob controles de segurança rigorosos dos sistemas do [Armazenamento do Microsoft Azure](https://azure.microsoft.com/services/storage/) seguros.

A equipe do .NET quer saber como as ferramentas são usadas e se elas estão funcionando bem, e não o que você está compilando com as ferramentas. Se você suspeita que a telemetria está coletando dados confidenciais ou que os dados estão sendo manipulados de modo inseguro ou inadequado, registre um problema no repositório [dotnet/cli](https://github.com/dotnet/cli/issues) para investigação.

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

&#8225;Normalmente, a coluna *Geografia* exibe o nome de um país/região. Em alguns casos, continente da Antártida aparece na coluna, devido ao fato de os pesquisadores usarem o .NET Core na Antártida ou a dados de localização incorretos.

### <a name="example"></a>Exemplo

| Timestamp      | Ocorrências | Comando | Geografia | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | executar     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Conjuntos de dados

- [2016 – T3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [2016 – T4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [2017 – T1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [2017 – T2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [2017 – T3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [2017 – T4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

Outros conjuntos de dados são publicados usando um formato de URL padrão. Substitua `<YEAR>` pelo ano e substitua `<QUARTER>` pelo trimestre do ano (use `1`, `2`, `3` ou `4`). Os arquivos estão no formato *TSV* (valores separados por tabulação).

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licença

A distribuição da Microsoft do .NET Core é licenciada com os [Termos de licença de software da Microsoft: biblioteca do Microsoft .NET](https://aka.ms/dotnet-core-eula). Para obter detalhes sobre a coleta e o processamento de dados, veja a seção intitulada "Dados".

Os [Pacotes NuGet do .NET](https://www.nuget.org/profiles/dotnetframework) usam essa mesma licença, mas não habilitam a telemetria (consulte o [Escopo](#scope)).

## <a name="disclosure"></a>Divulgação

O SDK do .NET Core exibe o texto a seguir quando você executa pela primeira vez um dos [comandos da CLI do .NET Core](index.md) (por exemplo, `dotnet restore`). O texto pode variar um pouco dependendo da versão do SDK que você está executando. Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Consulte também

- [O que aprendemos com a telemetria do SDK do .NET Core](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/)
- [Fonte de referência de telemetria (repositório dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [Dados de uso do SDK do .NET Core](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md)
