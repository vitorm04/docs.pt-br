---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503649"
---
# <a name="dotnet-pack"></a>dotnet pack

**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet pack` – Empacota o código em um pacote NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet pack` compila o projeto e cria pacotes NuGet. O resultado deste comando é um pacote NuGet (ou seja, um arquivo *.nupkg).*

Se você quiser gerar um pacote que contenha os símbolos de depuração, você tem duas opções disponíveis:

- `--include-symbols`- cria o pacote de símbolos.
- `--include-source`- ele cria o pacote `src` de símbolos com uma pasta dentro contendo os arquivos de origem.

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

## <a name="arguments"></a>Argumentos

`PROJECT | SOLUTION`

  O projeto ou solução para embalar. Ou é um caminho para um [arquivo csproj,](csproj.md)um arquivo de solução ou para um diretório. Se não for especificado, o comando pesquisa o diretório atual para um arquivo de projeto ou solução.

## <a name="options"></a>Opções

- **`-c|--configuration <CONFIGURATION>`**

  Define a configuração da compilação. O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.

- **`--force`**

  Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

- **`-h|--help`**

  Imprime uma ajuda breve para o comando.

- **`--include-source`**

  Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída. Os arquivos de fontes `src` estão incluídos na pasta dentro do pacote de símbolos.

- **`--include-symbols`**

  Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída.

- **`--interactive`**

  Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação). Disponível desde o SDK do .NET Core 3.0.

- **`--no-build`**

  Não compila o projeto antes do empacotamento. Também define o sinalizador `--no-restore` implicitamente.

- **`--no-dependencies`**

  Ignora as referências projeto a projeto e só restaura o projeto raiz.

- **`--no-restore`**

  Não executa uma restauração implícita ao executar o comando.

- **`--nologo`**

  Não exibe a faixa de inicialização nem a mensagem de direitos autorais. Disponível desde o SDK do .NET Core 3.0.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Coloca os pacotes compilados no diretório especificado.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Especifica o runtime de destino para o qual restaurar os pacotes. Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).

- **`-s|--serviceable`**

  Define o sinalizador operacional no pacote. Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.

- **`-v|--verbosity <LEVEL>`**

  Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

- Empacota o projeto no diretório atual:

  ```dotnetcli
  dotnet pack
  ```

- Empacote o projeto `app1`:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Embale o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Empacotar o projeto, usando um [arquivo .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
