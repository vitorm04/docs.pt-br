---
title: Comando dotnet vstest – CLI do .NET Core
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
author: guardrex
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: e11b193ff7a8c639078c5cf279b7fbbeab553c92
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet-vstest` - Executa testes a partir de arquivos especificados.

## <a name="synopsis"></a>Sinopse

`dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]`

## <a name="description"></a>Descrição

O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade e testes de aplicativo de IU codificado.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Execute testes a partir de assemblies especificados. Separe vários nomes de assembly de teste com espaços.

## <a name="options"></a>Opções

`--Settings|/Settings:<Settings File>`

Configurações para usar ao executar testes.

`--Tests|/Tests:<Test Names>`

Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

`--TestAdapterPath|/TestAdapterPath`

Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

`--Platform|/Platform:<Platform type>`

Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

`--Framework|/Framework:<Framework Version>`

Versão do .NET Framework de destino usada na execução de teste. Os exemplos de valores válidos são `.NETFramework,Version=v4.6`, `.NETCoreApp,Version=v1.0` etc. Outros valores com suporte são `Framework35`, `Framework40`, `Framework45` e `FrameworkCore10`.

`--Parallel|/Parallel`

Execute testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Defina um número explícito de núcleos com um arquivo de configurações.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`.  O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Os parênteses `()` são usados para agrupar subexpressões.

`-?|--Help|/?|/Help`

Imprime uma ajuda breve para o comando.

`--logger|/logger:<Logger Uri/FriendlyName>`

Especificar um agente para resultados do teste.  

* Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:

  ```
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`. Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado. Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.

  ```
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

Lista testes descobertos do contêiner de teste fornecido.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID de processo do processo pai responsável por iniciar o processo atual.

`--Port|/Port:<Port>`

Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

`--Diag|/Diag:<Path to log file>`

Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

`args`

Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

## <a name="examples"></a>Exemplos

Execute testes em `mytestproject.dll`:

`dotnet vstest mytestproject.dll`

Executar testes em `mytestproject.dll`, exportando para uma pasta personalizada com um nome personalizado:

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

Execute testes em `mytestproject.dll` e `myothertestproject.exe`:

`dotnet vstest mytestproject.dll myothertestproject.exe`

Execute testes `TestMethod1`:

`dotnet vstest /Tests:TestMethod1`

Execute testes `TestMethod1` e `TestMethod2`:

`dotnet vstest /Tests:TestMethod1,TestMethod2`

