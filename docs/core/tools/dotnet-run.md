---
title: Comando dotnet run – CLI do .NET Core
description: O comando dotnet run oferece uma opção conveniente para executar o aplicativo do código-fonte.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47235488"
---
# <a name="dotnet-run"></a>dotnet run

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nome

`dotnet run` – Executa o código-fonte sem qualquer comando de compilação ou inicialização explícito.

## <a name="synopsis"></a>Sinopse

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a>Descrição

O comando `dotnet run` fornece uma opção conveniente para executar o aplicativo do código-fonte com um comando. Ele é útil para o desenvolvimento iterativo rápido a partir da linha de comando. O comando depende do comando [`dotnet build`](dotnet-build.md) para compilar o código. Os requisitos para a compilação, como o projeto, devem ser restaurado primeiro, e se aplicam a `dotnet run` também.

Os arquivos de saída são gravados no local padrão, que é `bin/<configuration>/<target>`. Por exemplo, se você tiver um aplicativo `netcoreapp2.1` e executar `dotnet run`, a saída será colocada em `bin/Debug/netcoreapp2.1`. Os arquivos são substituídos conforme necessário. Os arquivos temporários são colocados no diretório `obj`.

Se o projeto especificar várias estruturas, a execução de `dotnet run` resultará em um erro, a menos que a opção `-f|--framework <FRAMEWORK>` seja usada para especificar a estrutura.

O comando `dotnet run` é usado no contexto de projetos, não assemblies compilados. Se, em vez disso, você estiver tentando executar uma DLL de aplicativo dependente da estrutura, use [dotnet](dotnet.md) sem um comando. Por exemplo, para executar `myapp.dll`, use:

```console
dotnet myapp.dll
```

Para saber mais sobre o driver `dotnet`, veja o tópico [CLI (Ferramentas de Linha de Comando) do .NET Core](index.md).

Para executar o aplicativo, o comando `dotnet run` resolve as dependências do aplicativo que estão fora do tempo de execução compartilhado por meio do cache NuGet. Como ele usa as dependências em cache, não recomendamos usar `dotnet run` para executar aplicativos em produção. Em vez disso, [crie uma implantação](../deploying/index.md) usando o comando [`dotnet publish`](dotnet-publish.md) e implante a saída publicada.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Opções

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada. A estrutura deve ser especificada no arquivo de projeto.

`--force`

Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--launch-profile <NAME>`

O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo. Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`. Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).

`--no-build`

Não compila o projeto antes da execução. Também define o sinalizador `--no-restore` implicitamente.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.

`--no-launch-profile`

Não tenta usar *launchSettings.json* para configurar o aplicativo.

`--no-restore`

Não executa uma restauração implícita ao executar o comando.

`-p|--project <PATH>`

Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo). Se não é especificado, ele usa como padrão o diretório atual.

`--runtime <RUNTIME_IDENTIFIER>`

Especifica o tempo de execução de destino para o qual restaurar os pacotes. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada. A estrutura deve ser especificada no arquivo de projeto.

`--force`

Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida. A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.

`-h|--help`

Imprime uma ajuda breve para o comando.

`--launch-profile <NAME>`

O nome do perfil de inicialização (se houver) a ser usado ao iniciar o aplicativo. Os perfis de inicialização são definidos no arquivo *launchSettings.json* e, normalmente, são chamados `Development`, `Staging` e `Production`. Para obter mais informações, consulte [Working with multiple environments](/aspnet/core/fundamentals/environments) (Trabalhando com vários ambientes).

`--no-build`

Não compila o projeto antes da execução. Também define o sinalizador `--no-restore` implicitamente.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.

`--no-launch-profile`

Não tenta usar *launchSettings.json* para configurar o aplicativo.

`--no-restore`

Não executa uma restauração implícita ao executar o comando.

`-p|--project <PATH>`

Especifica o caminho do arquivo de projeto a ser executado (nome da pasta ou caminho completo). Se não é especificado, ele usa como padrão o diretório atual.

`--runtime <RUNTIME_IDENTIFIER>`

Especifica o tempo de execução de destino para o qual restaurar os pacotes. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Delimita os argumentos para `dotnet run` dos argumentos para o aplicativo que está sendo executado. Todos os argumentos após esse delimitador são passados para o aplicativo que está sendo executado.

`-c|--configuration {Debug|Release}`

Define a configuração da compilação. O valor padrão é `Debug`.

`-f|--framework <FRAMEWORK>`

Compila e executa o aplicativo usando a [estrutura](../../standard/frameworks.md) especificada. A estrutura deve ser especificada no arquivo de projeto.

`-h|--help`

Imprime uma ajuda breve para o comando.

`-p|--project <PATH/PROJECT.csproj>`

Especifica o caminho e o nome do arquivo de projeto. (Consulte a OBSERVAÇÃO.) Se não é especificado, ele usa como padrão o diretório atual.

> [!NOTE]
> Use o caminho e o nome do arquivo de projeto com a opção `-p|--project`. Uma regressão na CLI impede o fornecimento de um caminho de pasta com o SDK do .NET Core 1. x. Para obter mais informações sobre esse problema, consulte [dotnet run -p, não é possível iniciar um projeto (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Exemplos

Execute o projeto no diretório atual:

`dotnet run`

Execute o projeto especificado:

`dotnet run --project ./projects/proj1/proj1.csproj`

Execute o projeto no diretório atual (o argumento `--help` neste exemplo é passado para o aplicativo, visto que a opção vazia `--` foi usada):

`dotnet run --configuration Release -- --help`

Restaure as dependências e as ferramentas para o projeto no diretório atual, apenas mostrando uma saída mínima e, em seguida, execute o projeto (SDK do .NET Core 2.0 e versões posteriores):

`dotnet run --verbosity m`