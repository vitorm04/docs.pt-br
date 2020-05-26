---
title: Comando dotnet test
description: O comando dotnet test é usado para executar testes de unidade em um determinado projeto.
ms.date: 04/29/2020
ms.openlocfilehash: 22b27007d26c98cff40733ef8d449ce334f87848
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802687"
---
# <a name="dotnet-test"></a>dotnet test

**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores

## <a name="name"></a>Nome

`dotnet test` - driver de teste do .NET usado para executar testes de unidade.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
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

O `dotnet test` comando é usado para executar testes de unidade em uma determinada solução. O `dotnet test` comando cria a solução e executa um aplicativo de host de teste para cada projeto de teste na solução. O host de teste executa testes no projeto fornecido usando uma estrutura de teste, por exemplo: MSTest, NUnit ou xUnit, e relata o êxito ou a falha de cada teste. Se todos os testes forem bem-sucedidos, o executor de testes retornará 0 como um código de saída; caso contrário, se algum teste falhar, retornará 1.

Para projetos de vários destinos, os testes são executados para cada estrutura de destino. O host de teste e a estrutura de teste de unidade são empacotados como pacotes NuGet e restaurados como dependências comuns para o projeto.

Os projetos de teste especificam o executor de teste usando um elemento comum `<PackageReference>`, conforme mostrado no exemplo de arquivo de projeto a seguir:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

Onde `Microsoft.NET.Test.Sdk` é o host de teste, `xunit` é a estrutura de teste. E `xunit.runner.visualstudio` é um adaptador de teste, que permite que a estrutura xUnit funcione com o host de teste.

### <a name="implicit-restore"></a>Restauração implícita

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumentos

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - Caminho para o projeto de teste.
  - Caminho para a solução.
  - Caminho para um diretório que contém um projeto ou uma solução.
  - Caminho para um arquivo *. dll* do projeto de teste.

  Se não for especificado, ele pesquisará um projeto ou uma solução no diretório atual.

## <a name="options"></a>Opções

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Caminho para um diretório a ser procurado para os adaptadores de teste adicionais. Somente arquivos *. dll* com sufixo `.TestAdapter.dll` são inspecionados. Se não for especificado, o diretório do test *. dll* será pesquisado.

- **`--blame`**

  Executa os testes no modo blame. Essa opção é útil para isolar testes problemáticos que causam falha no host de teste. Quando uma falha é detectada, ela cria um arquivo de sequência no `TestResults/<Guid>/<Guid>_Sequence.xml` que captura a ordem dos testes que foram executados antes da falha.

- **`-c|--configuration <CONFIGURATION>`**

  Define a configuração da compilação. O valor padrão é `Debug`, mas a configuração do seu projeto pode substituir essa configuração padrão do SDK.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Habilita o coletor de dados para a execução de teste. Para obter mais informações, consulte [Monitor and analyze test run](https://aka.ms/vstest-collect) (Monitorar e analisar a execução de teste).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Habilita o modo de diagnóstico para a plataforma de teste e grava mensagens de diagnóstico no arquivo especificado e nos arquivos ao lado dele. O processo que está registrando as mensagens determina quais arquivos são criados, como `*.host_<date>.txt` para o log do host de teste e `*.datacollector_<date>.txt` para o log do coletor de dados.

- **`-f|--framework <FRAMEWORK>`**

  Força o uso de `dotnet` ou .NET Framework host de teste para os binários de teste. Essa opção determina apenas o tipo de host a ser usado. A versão real do Framework a ser usada é determinada pelo *runtimeconfig. JSON* do projeto de teste. Quando não especificado, o [atributo de assembly TargetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) é usado para determinar o tipo de host. Quando esse atributo é removido do *. dll*, o host de .NET Framework é usado.

- **`--filter <EXPRESSION>`**

  Filtra os testes no projeto atual usando a expressão especificada. Para saber mais, confira a seção [Filtrar detalhes da opção](#filter-option-details). Para obter mais informações e exemplos sobre como usar a filtragem de teste de unidade seletivo, confira [Executando testes de unidade seletivos](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--interactive`**

  Permite que o comando pare e aguarde entrada ou ação do usuário. Por exemplo, para concluir a autenticação. Disponível desde o SDK do .NET Core 3.0.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Especifica um agente para resultados do teste. Ao contrário do MSBuild, o teste dotnet não aceita abreviações: em vez de `-l "console;v=d"` usar `-l "console;verbosity=detailed"` .

- **`--no-build`**

  Não compila o projeto de teste antes de sua execução. Ele também define implicitamente o- `--no-restore` Flag.

- **`--nologo`**

  Executar testes sem exibir o banner do Microsoft TestPlatform. Disponível desde o SDK do .NET Core 3.0.

- **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Diretório no qual encontram-se os binários para execução. Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.  Para projetos com várias estruturas de destino (por meio da `TargetFrameworks` Propriedade), também é necessário definir `--framework` quando você especifica essa opção. `dotnet test`sempre executa testes do diretório de saída. Você pode usar <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> para consumir ativos de teste no diretório de saída.

- **`-r|--results-directory <PATH>`**

  O diretório em que os resultados de teste serão colocados. Se o diretório especificado não existir, ele será criado. O padrão é `TestResults` o diretório que contém o arquivo de projeto.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  O tempo de execução de destino para o qual testar.

- **`-s|--settings <SETTINGS_FILE>`**

  O arquivo `.runsettings` a ser usado para executar os testes. Observe que o `TargetPlatform` elemento (x86 | x64) não tem nenhum efeito para `dotnet test` . Para executar testes direcionados para x86, instale a versão x86 do .NET Core. O bit de bits do *dotnet. exe* que está no caminho é o que será usado para executar testes. Para saber mais, consulte os recursos a seguir:

  - [Configurar testes de unidade usando um arquivo `.runsettings`.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Configurar uma execução de teste](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Lista todos os testes descobertos no projeto atual.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O padrão é `minimal`. Para obter mais informações, consulte <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** argumentos

 Inline `RunSettings` são passados como os últimos argumentos na linha de comando após "--" (Observe o espaço após--). Inline `RunSettings` são especificados como `[name]=[value]` pares. Um espaço é usado para separar vários pares `[name]=[value]`.

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
  
  - Execute os testes no projeto no diretório atual e relate os testes que estavam em andamento quando o host de teste falhou:

  ```dotnetcli
  dotnet test --blame
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
