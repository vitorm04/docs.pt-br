---
title: Comando dotnet build
description: O comando dotnet build compila um projeto e todas as suas dependências.
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632129"
---
# <a name="dotnet-build"></a>dotnet build

**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nome

`dotnet build` – Compila um projeto e todas as suas dependências.

## <a name="synopsis"></a>Sinopse

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários. Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*. Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo. O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.

Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto. Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução. Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado. Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md). Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).

A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo. O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado. Sem o arquivo de ativos em vigor, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros. Com o SDK do .NET Core 1.x, você precisava executar explicitamente o `dotnet restore` antes de executar `dotnet build`. Começando pelo SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente quando você executa `dotnet build`. Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto. O seguinte exemplo mostra um projeto que produz um código executável:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Para produzir uma biblioteca, omita a propriedade `<OutputType>`. A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.

### <a name="msbuild"></a>MSBuild

O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais. Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).

Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente. Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Ou você também pode usar o comando [dotnet msbuild](dotnet-msbuild.md).

A execução de `dotnet build` é equivalente a `dotnet msbuild -restore -target:Build`.

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

O arquivo de projeto ou solução a ser compilado. Se um arquivo de solução ou projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tenha uma extensão terminada em *proj* ou *sln* e usará esse arquivo.

## <a name="options"></a>Opções

* **`-c|--configuration {Debug|Release}`**

  Define a configuração da compilação. O valor padrão é `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Compila para uma [estrutura](../../standard/frameworks.md) específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

* **`--force`**

  Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*. Disponível desde o SDK do .NET Core 2.0.

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

* **`--interactive`**

  Permite que o comando pare e aguarde entrada ou ação do usuário. Por exemplo, para concluir a autenticação. Disponível desde o SDK do .NET Core 3.0.

* **`--no-dependencies`**

  Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.

* **`--no-incremental`**

  Marca o build como não segura para build incremental. Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.

* **`--no-logo`**

  Não exibe a faixa de inicialização nem a mensagem de direitos autorais. Disponível desde o SDK do .NET Core 3.0.

* **`--no-restore`**

  Não executa uma restauração implícita durante o build. Disponível desde o SDK do .NET Core 2.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção. Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Especifica o tempo de execução de destino. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhamento do MSBuild. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O padrão é `minimal`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Define o valor da propriedade `$(VersionSuffix)` a ser usada ao compilar o projeto. Isso funcionará apenas se a propriedade `$(Version)` não estiver definida. Em seguida, `$(Version)` é definido como o `$(VersionPrefix)` combinado com o `$(VersionSuffix)`, separado por um traço.

## <a name="examples"></a>Exemplos

* Compile um projeto e suas dependências:

  ```console
  dotnet build
  ```

* Compile um projeto e suas dependências usando a configuração da Versão:

  ```console
  dotnet build --configuration Release
  ```

* Compile um projeto e suas dependências para um tempo de execução específico (no exemplo, Ubuntu 18.04):

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Compile o projeto e use a fonte do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Compile o projeto e defina a versão 1.2.3.4 como um parâmetro de compilação:

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
