---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: a8218b6596601069b89a60ad018adf89a1f47cf6
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624885"
---
# <a name="dotnet-test"></a>dotnet test

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet test` - driver de teste do .NET usado para executar testes de unidade.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Descrição

O comando `dotnet test` é usado para executar testes de unidade em um determinado projeto. O comando `dotnet test` inicia o aplicativo de console executor de teste especificado para um projeto. O executor de teste realiza os testes definidos para uma estrutura de teste de unidade (por exemplo, MSTest, NUnit ou xUnit) e relata o êxito ou a falha de cada teste. Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1. Para projetos de vários destinos, os testes são executados para cada estrutura de destino. O executor de teste e a biblioteca de teste de unidade são empacotados como pacotes NuGet e são restaurados como dependências comuns para o projeto.

Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

### <a name="implicit-restore"></a>Restauração implícita

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumentos

- **`PROJECT | SOLUTION`**

  Caminho para o projeto de teste ou solução. Se não é especificado, usa como padrão o diretório atual.

## <a name="options"></a>Opções

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Usa os adaptadores de teste personalizado do caminho especificado na execução de teste.

- **`--blame`**

  Executa os testes no modo blame. Essa opção é útil para isolar testes problemáticos que causam falha no host de teste. Ela cria um arquivo de saída no diretório atual como *Sequence.xml* que captura a ordem de execução dos testes antes da falha.

- **`-c|--configuration <CONFIGURATION>`**

  Define a configuração da compilação. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Habilita o coletor de dados para a execução de teste. Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Habilita o modo de diagnóstico para a plataforma de teste e grava as mensagens de diagnóstico no arquivo especificado.

- **`-f|--framework <FRAMEWORK>`**

  Procura os binários de teste para uma [estrutura](../../standard/frameworks.md) específica.

- **`--filter <EXPRESSION>`**

  Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--interactive`**

  Permite que o comando pare e aguarde entrada ou ação do usuário. Por exemplo, para concluir a autenticação. Disponível desde o SDK do .NET Core 3.0.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Especifica um agente para resultados do teste. Ao contrário do MSBuild, o teste dotnet não aceita abreviações `-l "console;v=d"` : `-l "console;verbosity=detailed"`em vez de usar.

- **`--no-build`**

  Não compila o projeto de teste antes de sua execução. Ele também define implicitamente o- `--no-restore` Flag.

- **`--nologo`**

  Executar testes sem exibir o banner do Microsoft TestPlatform. Disponível desde o SDK do .NET Core 3.0.

- **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Diretório no qual encontram-se os binários para execução. Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.  Para projetos com várias estruturas de destino (por meio `TargetFrameworks` da propriedade), também é necessário definir `--framework` quando você especifica essa opção. `dotnet test`sempre execute testes do diretório de saída. Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.

- **`-r|--results-directory <PATH>`**

  O diretório em que os resultados de teste serão colocados. Se o diretório especificado não existir, ele será criado. O padrão é `TestResults` o diretório que contém o arquivo de projeto.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  O tempo de execução de destino para o qual testar.

- **`-s|--settings <SETTINGS_FILE>`**

  O arquivo `.runsettings` a ser usado para executar os testes. Observe que o `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito `dotnet test`para. Para executar testes direcionados para x86, instale a versão x86 do .NET Core. O bit de bits do *dotnet. exe* que está no caminho é o que será usado para executar testes. para obter mais informações, consulte os seguintes recursos:

  - [Configurar testes de unidade usando um arquivo `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Configurar uma execução de teste](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Lista todos os testes descobertos no projeto atual.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O padrão é `minimal`. Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** argumentos

  Os argumentos são passados `RunSettings` como configurações para o teste. Os argumentos são especificados como pares `[name]=[value]` após "-- " (observe o espaço após --). Um espaço é usado para separar vários pares `[name]=[value]`.

  Exemplo: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Para obter mais informações, consulte [passando argumentos RunSettings por meio da linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Exemplos

- Execute os testes no projeto no diretório atual:

  ```dotnetcli
  dotnet test
  ```

- Execute os testes no projeto `test1`:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Execute os testes no projeto no diretório atual e gere um arquivo de resultados de teste no formato TRX:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Execute os testes no projeto no diretório atual e faça logon com detalhes detalhados no console:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

## <a name="filter-option-details"></a>Filtrar detalhes da opção

`--filter <EXPRESSION>`

`<Expression>` tem o formato `<property><operator><value>[|&<Expression>]`.

`<property>` é um atributo de `Test Case`. A seguir estão as propriedades com suporte nas estruturas populares de teste de unidade:

| Estrutura de teste | Propriedades com suporte                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Nome</li><li>ClassName</li><li>Prioridade</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Características</li></ul>                                   |

O `<operator>` descreve a relação entre a propriedade o valor:

| Operador | Função        |
| :------: | --------------- |
| `=`      | Correspondência exata     |
| `!=`     | Sem correspondência exata |
| `~`      | Contém        |
| `!~`     | Não contém    |

`<value>` é uma cadeia de caracteres. As pesquisas não diferenciam maiúsculas de minúsculas.

Uma expressão sem um `<operator>` é automaticamente considerada como um `contains` na propriedade `FullyQualifiedName` (por exemplo, `dotnet test --filter xyz` é o mesmo que `dotnet test --filter FullyQualifiedName~xyz`).

As expressões podem ser associadas a operadores condicionais:

| Operador            | Função |
| ------------------- | -------- |
| <code>&#124;</code> | OU       |
| `&`                 | AND      |

Inclua expressões em parênteses ao usar operadores condicionais (por exemplo, `(Name~TestMethod1) | (Name~TestMethod2)`).

Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Confira também

- [Estruturas e destinos](../../standard/frameworks.md)
- [Catálogo do Identificador de Runtime do .NET Core](../rid-catalog.md)
- [Passando argumentos RunSettings por meio de linha de comando](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
