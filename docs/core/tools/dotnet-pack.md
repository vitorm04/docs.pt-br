---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 08/08/2019
ms.openlocfilehash: ba5a438d58963222c3fa55d2c585ef503dcd49db
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990419"
---
# <a name="dotnet-pack"></a>dotnet pack

**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nome

`dotnet pack` – Empacota o código em um pacote NuGet.

## <a name="synopsis"></a>Sinopse

```console
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado desse comando é um pacote NuGet (ou seja, um arquivo *. nupkg* ). 

Se você quiser gerar um pacote que contém os símbolos de depuração, terá duas opções disponíveis:

- `--include-symbols`-Ele cria o pacote de símbolos.
- `--include-source`-Ele cria o pacote de símbolos com `src` uma pasta dentro de contendo os arquivos de origem.

As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado. As referências de projeto a projeto não são empacotadas dentro do projeto. No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.

Por padrão, `dotnet pack` compila primeiro o projeto. Se você quiser evitar esse comportamento, passe a opção `--no-build`. Com frequência, essa opção é útil em cenários de build de CI (integração contínua) nos quais você sabe que o código foi compilado anteriormente.

Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento. Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). A seção [Exemplos](#examples) mostra como usar a opção -p do MSBuild para alguns cenários diferentes.

Projetos da Web não são empacotáveis por padrão. Para substituir o comportamento padrão, adicione a seguinte propriedade ao seu arquivo *.csproj*:

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Arguments

`PROJECT | SOLUTION`

  O projeto ou a solução a ser empacotada. É um caminho para um [arquivo csproj](csproj.md), um arquivo de solução ou um diretório. Se não for especificado, o comando pesquisará o diretório atual em busca de um arquivo de projeto ou de solução.

## <a name="options"></a>Opções

* **`-c|--configuration {Debug|Release}`**

  Define a configuração da compilação. O valor padrão é `Debug`.

* **`--force`**

  Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*. Opção disponível desde o SDK do .NET Core 2.0.

* **`-h|--help`**

  Imprime uma ajuda breve para o comando.

* **`--include-source`**

  Inclui os pacotes de depuração do NuGet, além dos pacotes NuGet regulares no diretório de saída. Os arquivos de origem são incluídos na `src` pasta dentro do pacote de símbolos.

* **`--include-symbols`**

  Inclui os pacotes de depuração do NuGet, além dos pacotes NuGet regulares no diretório de saída.

* **`--interactive`**

  Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação). Disponível desde o SDK do .NET Core 3.0.

* **`--no-build`**

  Não compila o projeto antes do empacotamento. Também define o sinalizador `--no-restore` implicitamente.

* **`--no-dependencies`**

  Ignora as referências projeto a projeto e só restaura o projeto raiz. Opção disponível desde o SDK do .NET Core 2.0.

* **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando. Opção disponível desde o SDK do .NET Core 2.0.

* **`--nologo`**

  Não exibe a faixa de inicialização nem a mensagem de direitos autorais. Disponível desde o SDK do .NET Core 3.0.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Coloca os pacotes compilados no diretório especificado.

* **`--runtime <RUNTIME_IDENTIFIER>`**

  Especifica o tempo de execução de destino para o qual restaurar os pacotes. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md). Opção disponível desde o SDK do .NET Core 2.0.

* **`-s|--serviceable`**

  Define o sinalizador operacional no pacote. Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.

* **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

* Empacota o projeto no diretório atual:

  ```console
  dotnet pack
  ```

* Empacote o projeto `app1`:

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:

  ```console
  dotnet pack --output nupkgs
  ```

* Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* Empacote o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):

  ```console
  dotnet pack --runtime win10-x64
  ```

* Empacotar o projeto, usando um [arquivo .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```console
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
