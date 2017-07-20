---
title: Telemetria de Ferramentas do .NET Core | Microsoft Docs
description: .NET Core
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 480df976-7568-4df4-9d26-9911357b5a31
ms.translationtype: Human Translation
ms.sourcegitcommit: 6f3dc4235c75d7438f019838cb22192f4dc7c41a
ms.openlocfilehash: b7de81f38c0d4fa259f1c9d8ada675197930e945
ms.contentlocale: pt-br
ms.lasthandoff: 05/30/2017

---

<a id="net-core-tools-telemetry" class="xliff"></a>

# Telemetria de Ferramentas do .NET Core

As Ferramentas do .NET Core incluem um [recurso de telemetria](https://github.com/dotnet/cli/pull/2145) que coleta informações de uso. É importante que a Equipe do .NET compreenda como as ferramentas estão sendo usadas para que possamos melhorá-las.

Os dados coletados são anônimos e serão publicados de forma agregada para ser usado pelos engenheiros da Microsoft e da comunidade sob a [Licença de Atribuição Creative Commons](https://creativecommons.org/licenses/by/4.0/).

<a id="scope" class="xliff"></a>

## Escopo

O comando `dotnet` é usado para iniciar aplicativos e as Ferramentas do .NET Core. O comando `dotnet` em si não realiza coletas da telemetria. São as Ferramentas do .NET Core executadas pelo comando `dotnet` que coletam a telemetria.

Comandos do .NET Core (telemetria desabilitada):

- `dotnet`
- `dotnet [path-to-app]`

[Comandos](index.md) das Ferramentas do .NET Core (telemetria habilitada), como:

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

<a id="behavior" class="xliff"></a>

## Comportamento

O recurso de telemetria das Ferramentas do .NET Core é habilitado por padrão. Você pode recusar o recurso de telemetria definindo uma variável de ambiente DOTNET_CLI_TELEMETRY_OPTOUT (por exemplo, `export` no macOS/Linux e `set` no Windows) como verdadeira (por exemplo, "true" ou 1).

<a id="data-points" class="xliff"></a>

## Pontos de Dados

O recurso coleta as seguintes partes de dados:

- O comando que está sendo usado (por exemplo, “build” ou “restore”)
- O ExitCode do comando
- Para projetos de teste, o executor de teste que está sendo usado
- O carimbo de data/hora da invocação
- A estrutura usada
- Se as IDs de tempo de execução estão presentes no nó “tempos de execução”
- A versão da CLI que está sendo usada

O recurso não coletará dados pessoais como nomes de usuário ou emails. Ele não verificará seu código e extrairá os dados de nível de projeto que podem ser considerados confidenciais, como nome, repositório ou autor (se forem definidos no seu project.json). Desejamos saber como as ferramentas são usadas, não o que você está criando com elas. Se você encontrar dados confidenciais que estão sendo coletados, isso será um bug. [Relate um problema](https://github.com/dotnet/cli/issues) e ele será corrigido.

<a id="license" class="xliff"></a>

## Licença

A distribuição da Microsoft do .NET Core é licenciada com o [EULA da MICROSOFT .NET LIBRARY](https://aka.ms/dotnet-core-eula). Isso inclui a seção “DADOS” impressa novamente abaixo para habilitar a telemetria.

[Pacotes NuGet .NET](https://www.nuget.org/profiles/dotnetframework) usam essa mesma licença, mas não habilitam a telemetria (veja o [Escopo](#scope) acima).

> 2. DADOS. O software pode coletar informações sobre você e seu uso do software e enviá-las para a Microsoft. A Microsoft pode usar essas informações para melhorar nossos produtos e serviços. Você pode saber mais sobre coleta e uso de dados na Documentação de Ajuda e na política de privacidade em http://go.microsoft.com/fwlink/?LinkId=528096. O uso do software serve como consentimento para essas práticas.

<a id="disclosure" class="xliff"></a>

## Divulgação

As Ferramentas do .NET Core exibem o texto a seguir quando você executa um dos comandos pela primeira vez (por exemplo, `dotnet restore`). Essa experiência de “primeira execução” é como a Microsoft notifica você sobre a coleta de dados. Essa mesma experiência também inicialmente popula seu cache NuGet com as bibliotecas no SDK do .NET Core, evitando solicitações para NuGet.org (ou outro feed do NuGet) para essas bibliotecas.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core @ https://aka.ms/dotnet-docs. Use dotnet --help to see available commands or go to https://aka.ms/dotnet-cli-docs.

Telemetry
--------------
The .NET Core tools collect usage data in order to improve your experience.
The data is anonymous and does not include command-line arguments. The data is collected by Microsoft and shared with the community.
You can opt out of telemetry by setting a DOTNET_CLI_TELEMETRY_OPTOUT environment variable to 1 using your favorite shell.
You can read more about .NET Core tools telemetry @ https://aka.ms/dotnet-cli-telemetry.

Configuring...
-------------------
A command is running to initially populate your local package cache, to improve restore speed and enable offline access. This command will take up to a minute to complete and will only happen once.
```

