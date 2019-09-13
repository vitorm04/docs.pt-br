---
title: Comando dotnet restore
description: Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore.
ms.date: 05/29/2018
ms.openlocfilehash: 567316e98e161a7645db6bf55a03c3c006999fa9
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893288"
---
# <a name="dotnet-restore"></a>dotnet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity] [--interactive]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Descrição

O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto. Por padrão, a restauração das dependências e as ferramentas são executadas em paralelo.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Para restaurar as dependências, o NuGet precisa dos feeds nos quais os pacotes estão localizados. Os feeds são geralmente fornecidos por meio do arquivo de configuração *nuget.config*. Um arquivo de configuração padrão é fornecido quando as ferramentas da CLI são instaladas. Especifique mais feeds criando seu próprio arquivo *nuget.config* no diretório do projeto. Também é possível especificar outros feeds por invocação em um prompt de comando.

Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`. Se não é especificado, o cache do pacote NuGet padrão é usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais. Por exemplo, */home/user1* no Linux ou *C:\Usuário\user1* no Windows.

Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.

### <a name="nugetconfig-differences"></a>Diferenças do nuget.config

O comportamento do comando `dotnet restore` será afetado pelas configurações no arquivo *nuget.config*, se estiver presente. Por exemplo, a definição da `globalPackagesFolder` em *nuget.config* coloca os pacotes NuGet restaurados na pasta especificada. Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`. Para obter mais informações, confira a [Referência do nuget.config](/nuget/schema/nuget-config-file).

Há três configurações específicas que são ignoradas por `dotnet restore`:

- [bindingRedirects](/nuget/schema/nuget-config-file#bindingredirects-section)

  Os redirecionamentos de associação não funcionam com elementos `<PackageReference>` e o .NET Core só dá suporte a elementos `<PackageReference>` em pacotes NuGet.

- [solution](/nuget/schema/nuget-config-file#solution-section)

  Essa configuração é específica do Visual Studio e não se aplica ao .NET Core. O .NET Core não usa um arquivo `packages.config` e, em vez disso, usa elementos `<PackageReference>` para pacotes NuGet.

- [trustedSigners](/nuget/schema/nuget-config-file#trustedsigners-section)

  Essa configuração não é aplicável, pois o [NuGet ainda não dá suporte à verificação de multiplataforma](https://github.com/NuGet/Home/issues/7939) de pacotes confiáveis.

## <a name="implicit-dotnet-restore"></a>`dotnet restore` implícito

Começando com o .NET Core 2.0, se necessário, o `dotnet restore` será executado implicitamente quando você executar os comandos a seguir:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Na maioria dos casos, você não precisa usar o comando `dotnet restore` explicitamente.

Às vezes, pode ser inconveniente executar `dotnet restore` implicitamente. Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede. Para evitar que o `dotnet restore` seja executado implicitamente, use o sinalizador `--no-restore` com um desses comandos para desabilitar a restauração implícita.

## <a name="arguments"></a>Arguments

`ROOT`

Caminho opcional para o arquivo de projeto a ser restaurado.

## <a name="options"></a>Opções

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.

`--disable-parallel`

Desabilita a restauração de vários projetos paralelamente.

`--force`

Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--ignore-failed-sources`

Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.

`--no-cache`

Especifica para não armazenar os pacotes e solicitações HTTP em cache.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.

`--packages <PACKAGES_DIRECTORY>`

Especifica o diretório para os pacotes restaurados.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica um tempo de execução para a restauração do pacote. Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md). Forneça diversas RIDs especificando essa opção várias vezes.

`-s|--source <SOURCE>`

Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração. Essa configuração substitui todas as fontes especificadas nos arquivos *nuget.config*. Diversas fontes podem ser fornecidas especificando essa opção várias vezes.

`--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

`--interactive`

Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação). A partir do .NET Core 2.1.400.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--configfile <FILE>`

O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.

`--disable-parallel`

Desabilita a restauração de vários projetos paralelamente.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--ignore-failed-sources`

Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.

`--no-cache`

Especifica para não armazenar os pacotes e solicitações HTTP em cache.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.

`--packages <PACKAGES_DIRECTORY>`

Especifica o diretório para os pacotes restaurados.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica um tempo de execução para a restauração do pacote. Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md). Forneça diversas RIDs especificando essa opção várias vezes.

`-s|--source <SOURCE>`

Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração. Isso substitui todas as fontes especificadas nos arquivos *NuGet. config* , lendo efetivamente o arquivo *NuGet. config* como se o `<packageSource>` elemento não estivesse lá. Diversas fontes podem ser fornecidas especificando essa opção várias vezes.

`--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

---

## <a name="examples"></a>Exemplos

Restaure as dependências e as ferramentas para o projeto no diretório atual:

`dotnet restore`

Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:

`dotnet restore ~/projects/app1/app1.csproj`

Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte:

`dotnet restore -s c:\packages\mypackages`

Restaure as dependências e as ferramentas para o projeto no diretório atual usando os caminhos dos dois arquivos fornecidos como fontes:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Restaure as dependências e as ferramentas do projeto no diretório atual e mostre apenas a saída mínima:

`dotnet restore --verbosity minimal`
