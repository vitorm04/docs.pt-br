---
title: Comando dotnet vstest
description: O comando dotnet vstest compila um projeto e todas as suas dependências.
ms.date: 02/27/2020
ms.openlocfilehash: 4941a6d08d45953039eb406a30f0ff984128ba1c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389625"
---
# <a name="dotnet-vstest"></a>dotnet vstest

**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet-vstest` - Executa testes a partir de arquivos especificados.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet vstest [<TEST_FILE_NAMES>] [--Blame] [--Diag]
    [--Framework] [--InIsolation] [-lt|--ListTests] [--logger]
    [--Parallel] [--ParentProcessId] [--Platform] [--Port]
    [--ResultsDirectory] [--Settings] [--TestAdapterPath]
    [--TestCaseFilter] [--Tests] [[--] <args>...]] [-?|--Help]
```

## <a name="description"></a>Descrição

O comando `dotnet-vstest` executa o aplicativo de linha de comando `VSTest.Console` para executar testes automatizados de unidade.

## <a name="arguments"></a>Argumentos

- **`TEST_FILE_NAMES`**

  Execute testes a partir de assemblies especificados. Separe vários nomes de assembly de teste com espaços. Há suporte para caracteres curinga.

## <a name="options"></a>Opções

- **`--Blame`**

  Executa os testes no modo blame. Essa opção é útil para isolar os testes problemáticos que causam uma falha do host de teste. Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.

- **`--Diag <Path to log file>`**

  Permite logs detalhados na plataforma de teste. Os logs são gravados no arquivo fornecido.

- **`--Framework <Framework Version>`**

  Versão do .NET Framework de destino usada na execução de teste. Alguns exemplos de valores válidos são `.NETFramework,Version=v4.6` ou `.NETCoreApp,Version=v1.0`. Outros valores com suporte são `Framework40`, `Framework45`, `FrameworkCore10` e `FrameworkUap10`.

- **`--InIsolation`**

  Executa os testes em um processo isolado. Isso torna o processo *vstest.console.exe* menos suscetível a ser interrompido por engano nos testes. Entretanto, os testes podem ser executados de forma mais lenta.

- **`-lt|--ListTests <File Name>`**

  Lista todos os testes descobertos do contêiner de teste fornecido.

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

- **`--Parallel`**

  Executar testes em paralelo. Por padrão, todos os núcleos disponíveis no computador estão disponíveis para uso. Especifique um número `MaxCpuCount` explícito de `RunConfiguration` núcleos definindo a propriedade sob o nó no arquivo *de configurações* de execução.

- **`--ParentProcessId <ParentProcessId>`**

  ID do processo pai responsável por iniciar o processo atual.

- **`--Platform <Platform type>`**

  Arquitetura da plataforma de destino usada para a execução de teste. Os valores válidos são `x86`, `x64` e `ARM`.

- **`--Port <Port>`**

  Especifica a porta para a conexão de soquete e recebimento das mensagens do evento.

- **`--ResultsDirectory:<PathToResulsDirectory>`**

  O diretório de resultados de teste será criado no caminho especificado, se não existir.

- **`--Settings <Settings File>`**

  Configurações para usar ao executar testes.

- **`--TestAdapterPath`**

  Use adaptadores de teste personalizados para um determinado caminho (se houver) na execução de teste.

- **`--TestCaseFilter <Expression>`**

  Execute testes que correspondam à expressão fornecida. `<Expression>` está no formato `<property>Operator<value>[|&<Expression>]`, onde Operator pode ser `=`, `!=` ou `~`. O operador `~` tem a semântica 'contains' e é aplicável para propriedades de cadeia de caracteres como `DisplayName`. Parênteses são usados `()` para agrupar subexpressões. Para obter mais informações, consulte [o filtro TestCase](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md).

- **`--Tests <Test Names>`**

  Execute testes com nomes que correspondam aos valores fornecidos. Separe vários valores com vírgulas.

- **`-?|--Help`**

  Imprime uma ajuda breve para o comando.

- **`@<file>`**

  Lê um arquivo de resposta para obter mais opções.

- **`args`**

  Especifica argumentos extras para passar ao adaptador. Os argumentos são especificados como pares de nome-valor no formato `<n>=<v>`, em que `<n>` é o nome de argumento e `<v>` é o valor do argumento. Use um espaço para separar vários argumentos.

## <a name="examples"></a>Exemplos

Executar testes em *mytestproject.dll*:

```dotnetcli
dotnet vstest mytestproject.dll
```

Executar testes em *mytestproject.dll,* exportando para pasta personalizada com nome personalizado:

```dotnetcli
dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path
```

Executar testes em *mytestproject.dll* e *myothertestproject.exe*:

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

## <a name="see-also"></a>Confira também

- [Opções da linha de comando de VSTest.Console.exe](/visualstudio/test/vstest-console-options)
