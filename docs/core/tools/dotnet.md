---
title: Comando dotnet - CLI do .NET Core | Microsoft Docs
description: "Saiba mais sobre o comando dotnet (o driver genérico para as ferramentas da CLI do .NET Core) e seu uso."
keywords: dotnet, CLI, comandos da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/20/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 256e468e-eaaa-4715-b5fb-8cbddcf80e69
translationtype: Human Translation
ms.sourcegitcommit: dff752a9d31ec92b113dae9eed20cd72faf57c84
ms.openlocfilehash: a470403e703ffb55de3d91cd5334c09bf11be06d
ms.lasthandoff: 03/22/2017

---

# <a name="dotnet-command"></a>Comando dotnet

## <a name="name"></a>Nome

`dotnet` – Driver geral para executar os comandos da linha de comando.

## <a name="synopsis"></a>Sinopse

`dotnet [command] [arguments] [--version] [--info] [-d|--diagnostics] [-v|--verbose] [--fx-version] [--additionalprobingpath] [-h|--help]`

## <a name="description"></a>Descrição

`dotnet` é um driver genérico para a cadeia de ferramentas da CLI (Interface de Linha de Comando). Invocado por conta própria, ele fornece breve instruções de uso.

Cada recurso específico é implementado como um comando. Para usar o recurso, o comando é especificado após `dotnet`, como [`dotnet build`](dotnet-build.md). Todos os argumentos após o comando são seus próprios argumentos.

A única vez que `dotnet` é usado como um comando em si é ao executar [aplicativos dependentes da estrutura](../app-types.md). Especifique uma DLL de aplicativo após o verbo `dotnet` para executar o aplicativo (por exemplo, `dotnet myapp.dll`).

## <a name="options"></a>Opções

`-v|--verbose`

Habilita a saída detalhada.

`-d|--diagnostics`

Habilita a saída de diagnóstico.

`--fx-version <VERSION>`

Versão do Framework Compartilhado instalada para usar a fim de executar o aplicativo.

`--additionalprobingpath <PATH>`

Caminho que contém a política de investigação e os assemblies a serem investigados.

`--version`

Imprime a versão das ferramentas de CLI.

`--info`

Imprime informações detalhadas sobre as ferramentas e o ambiente da CLI, como o sistema operacional atual, SHA de confirmação para a versão e outras informações.

`-h|--help`

Imprime uma ajuda breve para o comando. Se estiver com `dotnet`, também imprimirá uma lista de comandos disponíveis.

## <a name="dotnet-commands"></a>Comandos dotnet

### <a name="general"></a>Geral

Comando | Função
--- | ---
[dotnet-build](dotnet-build.md) | Compila um aplicativo .NET Core.
[dotnet-clean](dotnet-clean.md) | Limpa as saídas do build.
[dotnet-migrate](dotnet-migrate.md) | Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.
[dotnet-msbuild](dotnet-msbuild.md) | Oferece acesso à linha de comando do MSBuild.
[dotnet-new](dotnet-new.md) | Inicializa um projeto do C# ou F# de um modelo especificado.
[dotnet-pack](dotnet-pack.md) | Cria um pacote NuGet do seu código.
[dotnet-publish](dotnet-publish.md) | Publica um aplicativo dependente do .NET Framework ou autocontido.
[dotnet-restore](dotnet-restore.md) | Restaura as dependências para um determinado aplicativo.
[dotnet-run](dotnet-run.md) | Executa o aplicativo na origem.
[dotnet-sln](dotnet-sln.md) | Opções para adicionar, remover e listar projetos em um arquivo de solução.
[dotnet-test](dotnet-test.md) | Executa testes usando um executor de teste.

### <a name="project-references"></a>Referências de projeto

Comando | Função
--- | ---
[Referência dotnet-add](dotnet-add-reference.md) | Adicionar uma referência ao projeto.
[Referência dotnet-list](dotnet-list-reference.md) | Listar referências ao projeto.
[Referência dotnet-remove](dotnet-remove-reference.md) | Remover uma referência ao projeto.

### <a name="nuget-packages"></a>Pacotes NuGet

Comando | Função
--- | ---
[Pacote dotnet-add](dotnet-add-package.md) | Adicionar um pacote NuGet.
[Pacote dotnet-remove](dotnet-remove-package.md) | Remover um pacote NuGet.

### <a name="nuget-commands"></a>Comandos NuGet

Comando | Função
--- | ---
[dotnet-nuget delete](dotnet-nuget-delete.md) | Exclui ou retira da lista um pacote do servidor.
[dotnet-nuget locals](dotnet-nuget-locals.md) | Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.
[dotnet-nuget push](dotnet-nuget-push.md) | Envia um pacote ao servidor e os publica.

## <a name="examples"></a>Exemplos

Inicialize um aplicativo de console .NET Core de exemplo que pode ser compilado e executado:

`dotnet new console`

Restaure as dependências para um determinado aplicativo:

`dotnet restore`

Compile um projeto e suas dependências em um determinado diretório:

`dotnet build`

Execute um aplicativo dependente do framework chamado `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Variáveis de ambiente

`DOTNET_PACKAGES`

O cache do pacote principal. Se não estiver definido, o padrão será `$HOME/.nuget/packages` em Unix ou `%HOME%\NuGet\Packages` no Windows.

`DOTNET_SERVICING`

Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o tempo de execução.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft. Defina como `true` para cancelar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos); caso contrário, defina como `false` para cancelar os recursos de telemetria (os valores `false`, `0` ou `no`são aceitos). Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.

