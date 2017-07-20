---
title: Comando dotnet-restore - CLI do .NET Core | Microsoft Docs
description: "Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore."
keywords: dotnet-restore, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
ms.translationtype: Human Translation
ms.sourcegitcommit: 602c173ff8d114a76c5598cd0826485ac32a2e72
ms.openlocfilehash: fd4fd6ef2e8482a2b961ccbca1f5227d80c8be53
ms.contentlocale: pt-br
ms.lasthandoff: 03/29/2017

---

# <a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>Nome

`dotnet-restore` – Restaura as dependências e as ferramentas de um projeto.

## <a name="synopsis"></a>Sinopse

`dotnet restore [<ROOT>] [-s|--source] [-r|--runtime] [--packages] [--disable-parallel] [--configfile] [--no-cache] [--ignore-failed-sources] [--no-dependencies] [-v|--verbosity] [-h|--help]`

## <a name="description"></a>Descrição

O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto. Por padrão, a restauração das dependências e as ferramentas são feitas em paralelo.

Para restaurar as dependências, o NuGet precisa dos feeds de onde se encontram os pacotes. Os feeds são geralmente fornecidos por meio do arquivo de configuração *NuGet.config*. Um arquivo de configuração padrão é fornecido quando as ferramentas da CLI são instaladas. Especifique mais feeds criando seu próprio arquivo *NuGet.config* no diretório do projeto. Também é possível especificar outros feeds por invocação em um prompt de comando. 

Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`. Se não for especificado, o cache do pacote NuGet padrão será usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais (por exemplo, */home/user1* no Linux ou *C:\Usuários\user1* no Windows).

Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.

O comportamento do comando `dotnet restore` é afetado por algumas das configurações no arquivo *Nuget.Config*, se estiver presente. Por exemplo, definir o `globalPackagesFolder` em *NuGet.Config* coloca os pacotes NuGet restaurados na pasta especificada. Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`. Para obter mais informações, consulte a [Referência do NuGet.Config](https://docs.microsoft.com/nuget/schema/nuget-config-file).

## <a name="arguments"></a>Arguments

`ROOT` 
    
Caminho opcional para o arquivo de projeto a ser restaurado.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--source <SOURCE>`

Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração. Isso substitui todas as fontes especificadas nos arquivos *NuGet.config*. Diversas fontes podem ser fornecidas especificando essa opção várias vezes.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Especifica um tempo de execução para a restauração do pacote. Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*. Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md). Forneça diversas RIDs especificando essa opção várias vezes.

`--packages <PACKAGES_DIRECTORY>`

Especifica o diretório para os pacotes restaurados. 

`--disable-parallel`

Desabilita a restauração de vários projetos paralelamente. 

`--configfile <FILE>`

O arquivo de configuração NuGet (*NuGet.config*) a ser usado para a operação de restauração.

`--no-cache`

Especifica para não armazenar os pacotes e solicitações HTTP em cache.

`--ignore-failed-sources`

Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P (projeto a projeto), não restaure as referências, apenas o projeto raiz.

`--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

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

