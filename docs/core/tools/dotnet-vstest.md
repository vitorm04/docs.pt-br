---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
author: guardrex
ms.date: 05/30/2018
ms.openlocfilehash: dcf17a59fea1f58757f39721c5dd5947ed30df0f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613454"
---
# <a name="dotnet-vstest"></a>dotnet vstest

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet-vstest` - Executa testes a partir de arquivos especificados.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a>Descrição

O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.

## <a name="arguments"></a>Arguments

`TEST_FILE_NAMES`

Execute testes a partir de assemblies especificados. Separe vários nomes de assembly de teste com espaços.

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

Configurações para usar ao executar testes.

`--Tests|/Tests:<Test Names>`

Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

`--TestAdapterPath|/TestAdapterPath`

Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

`--Platform|/Platform:<Platform type>`

Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

`--Framework|/Framework:<Framework Version>`

Versão do .NET Framework de destino usada na execução de teste. Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.

`--Parallel|/Parallel`

Execute testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`. O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Os parênteses `()` são usados para agrupar subexpressões.

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

Lista todos os testes descobertos do contêiner de teste fornecido.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID do processo pai responsável por iniciar o processo atual.

`--Port|/Port:<Port>`

Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

`--Diag|/Diag:<Path to log file>`

Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

`--Blame|/Blame`

Executa os testes no modo blame. Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste. Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.

`--InIsolation|/InIsolation`

Executa os testes em um processo isolado. Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.

`@<file>`

Lê um arquivo de resposta para obter mais opções.

`args`

Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

Configurações para usar ao executar testes.

`--Tests|/Tests:<Test Names>`

Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

`--TestAdapterPath|/TestAdapterPath`

Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

`--Platform|/Platform:<Platform type>`

Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

`--Framework|/Framework:<Framework Version>`

Versão do .NET Framework de destino usada na execução de teste. Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Outros valores com suporte são `Framework40`, `Framework45` e `FrameworkCore10`.

`--Parallel|/Parallel`

Execute testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`. O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Os parênteses `()` são usados para agrupar subexpressões.

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

Lista todos os testes descobertos do contêiner de teste fornecido.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID do processo pai responsável por iniciar o processo atual.

`--Port|/Port:<Port>`

Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

`--Diag|/Diag:<Path to log file>`

Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

`args`

Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

Configurações para usar ao executar testes.

`--Tests|/Tests:<Test Names>`

Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

`--TestAdapterPath|/TestAdapterPath`

Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

`--Platform|/Platform:<Platform type>`

Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

`--Framework|/Framework:<Framework Version>`

Versão do .NET Framework de destino usada na execução de teste. Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Outros valores com suporte são `Framework40`, `Framework45` e `FrameworkCore10`.

`--Parallel|/Parallel`

Execute testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Especifique um número explícito de núcleos definindo a propriedade MaxCpuCount sob o nó RunConfiguration no arquivo runsettings.

`--TestCaseFilter|/TestCaseFilter:<Expression>`

Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`. O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Os parênteses `()` são usados para agrupar subexpressões.

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

Lista todos os testes descobertos do contêiner de teste fornecido.

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

ID do processo pai responsável por iniciar o processo atual.

`--Port|/Port:<Port>`

Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

`--Diag|/Diag:<Path to log file>`

Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

`args`

Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

---

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
