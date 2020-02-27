---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
ms.date: 05/30/2018
ms.openlocfilehash: fc0aa4f9abf069f78e27692ee84aea2559109c98
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626015"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>{1&gt;Nome&lt;1}

`dotnet-vstest` - Executa testes a partir de arquivos especificados.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Settings] [--Tests]
    [--TestAdapterPath] [--Platform] [--Framework] [--Parallel]
    [--TestCaseFilter] [--logger] [-lt|--ListTests]
    [--ParentProcessId] [--Port] [--Diag] [--Blame]
    [--InIsolation] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Descrição

O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.

## <a name="arguments"></a>Argumentos

- **`TEST_FILE_NAMES`**

  Execute testes a partir de assemblies especificados. Separe vários nomes de assembly de teste com espaços. Há suporte para caracteres curinga.

## <a name="options"></a>{1&gt;Opções&lt;1}

- **`--Settings <Settings File>`**

  Configurações para usar ao executar testes.

- **`--Tests <Test Names>`**

  Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

- **`--TestAdapterPath`**

  Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

- **`--Platform <Platform type>`**

  Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

- **`--Framework <Framework Version>`**

  Versão do .NET Framework de destino usada na execução de teste. Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.

- **`--Parallel`**

  Execute testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Especifique um número explícito de núcleos definindo a propriedade `MaxCpuCount` sob o nó `RunConfiguration` no arquivo *RunSettings* .

- **`--TestCaseFilter <Expression>`**

  Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`. O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Os `()` de parênteses são usados para agrupar subexpressões.

- **`-?|--Help`**

  Imprime uma ajuda breve para o comando.

- **`--logger <Logger Uri/FriendlyName>`**

  Especificar um agente para resultados do teste.

  - Para publicar resultados do teste no Team Foundation Server, use o provedor de agente `TfsPublisher`:

    ```console
    /logger:TfsPublisher;
        Collection=<team project collection url>;
        BuildName=<build name>;
        TeamProject=<team project name>
        [;Platform=<Defaults to "Any CPU">]
        [;Flavor=<Defaults to "Debug">]
        [;RunTitle=<title>]
    ```

  - Para registrar os resultados em um arquivo TRX (Resultados do teste) do Visual Studio, use o provedor de agente `trx`. Essa opção cria um arquivo no diretório dos resultados do teste com o nome de arquivo de log determinado. Se `LogFileName` não for fornecido, será criado um nome de arquivo exclusivo para armazenar os resultados do teste.

    ```console
    /logger:trx [;LogFileName=<Defaults to unique file name>]
    ```

- **`-lt|--ListTests <File Name>`**

  Lista todos os testes descobertos do contêiner de teste fornecido.

- **`--ParentProcessId <ParentProcessId>`**

  ID do processo pai responsável por iniciar o processo atual.

- **`--Port <Port>`**

  Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

- **`--Diag <Path to log file>`**

  Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

- **`--Blame`**

  Executa os testes no modo blame. Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste. Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.

- **`--InIsolation`**

  Executa os testes em um processo isolado. Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.

- **`@<file>`**

  Lê um arquivo de resposta para obter mais opções.

- **`args`**

  Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

## <a name="examples"></a>Exemplos

Executar testes em *MyTestProject. dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Execute testes em *MyTestProject. dll*, exportando para a pasta personalizada com o nome personalizado:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Execute testes em *MyTestProject. dll* e *myothertestproject. exe*:

```dotnetcli
dotnet vstest mytestproject.dll myothertestproject.exe
```

Execute testes `TestMethod1`:

```dotnetcli
dotnet vstest /Tests:TestMethod1
```

Execute testes `TestMethod1` e `TestMethod2`:

```dotnetcli
dotnet vstest /Tests:TestMethod1,TestMethod2
```
