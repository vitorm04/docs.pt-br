---
title: Comando dotnet-restore | Microsoft Docs
description: "Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore."
keywords: dotnet-restore, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fd7a5769-afbe-4838-bbaf-3ae0cfcbb914
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: a55cd932045a59f08146dff367a87eb6fe61f6e5
ms.lasthandoff: 03/07/2017

---

#<a name="dotnet-restore"></a>dotnet-restore

## <a name="name"></a>Nome

`dotnet-restore` – Restaura as dependências e as ferramentas de um projeto.

## <a name="synopsis"></a>Sinopse

```
dotnet restore [root] [-s|--source] [-r|--runtime] [--packages] [--disable-parallel] [--configfile] [--no-cache] [--ignore-failed-sources] [--no-dependencies] [-v|--verbosity]
dotnet restore [-h|--help]
```

## <a name="description"></a>Descrição

O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto. Por padrão, a restauração das dependências e ferramentas são feitas em paralelo.

Para restaurar as dependências, o NuGet precisa dos feeds de onde se encontram os pacotes. Os feeds geralmente são fornecidos por meio do arquivo de configuração NuGet; um padrão um está presente quando as ferramentas da CLI são instaladas. Você pode especificar mais feeds criando seu próprio arquivo NuGet.config no diretório do projeto. Os feeds também podem ser especificados por invocação no prompt de comando. 

Para dependências, você pode especificar onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`. Se não for especificado, o cache do pacote NuGet padrão será usado. Ele é encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais (por exemplo, */home/user1* no Linux ou *C:\Usuários\user1* no Windows).

Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.

## <a name="options"></a>Opções

`root` 
    
Caminho opcional para o arquivo de projeto a ser restaurado. 

`-h|--help`

Imprime uma ajuda breve para o comando.

`-s|--source <SOURCE>`

Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração. Isso substitui todas as fontes especificadas nos arquivos NuGet.config. Diversas fontes podem ser fornecidas especificando essa opção várias vezes.

`--packages <PACKAGES_DIRECTORY]`

Especifica o diretório no qual os pacotes restaurados serão colocados. 

`--disable-parallel`

Desabilita a restauração de vários projetos paralelamente. 

`--configfile <FILE>`

O arquivo de configuração NuGet (NuGet.config) a ser usado para a operação de restauração.

`--no-cache`

Especifica para não armazenar os pacotes e solicitações HTTP em cache.

` --ignore-failed-sources`

Somente avise sobre fontes com falha se houver pacotes que cumprem o requisito de versão.

`--no-dependencies`

Ao restaurar um projeto com referências de P2P, não restaure as referências, apenas o projeto raiz.

`--verbosity <LEVEL>`

Exibe essa quantidade de detalhes na saída. O nível pode ser `normal`, `quiet` ou `detailed`.

## <a name="examples"></a>Exemplos

Restaure as dependências e as ferramentas para o projeto no diretório atual:

`dotnet restore` 

Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:

`dotnet restore ~/projects/app1/app1.csproj`
    
Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte de fallback:

`dotnet restore -f c:\packages\mypackages` 

Restaure as dependências e as ferramentas para o projeto no diretório atual usando os dois caminhos de arquivo fornecidos como fontes de fallback:

`dotnet restore -f c:\packages\mypackages -f c:\packages\myotherpackages` 

Restaure as dependências e as ferramentas para o projeto no diretório atual, mostrando apenas os erros na saída:

`dotnet restore --verbosity Error`

