---
title: Comando dotnet-nuget-delete | Microsoft Docs
description: O comando dotnet-nuget-delete exclui ou retira da lista um pacote do servidor.
keywords: dotnet-nuget-delete, CLI, comando da CLI, .NET Core
author: karann-msft
ms.author: mairaw
ms.date: 11/11/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 6ddffde4-c789-4e90-990e-d35f6a6565d4
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 787b1427b1064943570cbc361042ab2f20d11088
ms.lasthandoff: 01/21/2017

---

#<a name="dotnet-nuget-delete"></a>dotnet-nuget-delete

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>Nome 
`dotnet-nuget-delete` – Exclui ou retira da lista um pacote do servidor. 

## <a name="synopsis"></a>Sinopse

`dotnet nuget delete [<package_name> <package_version>] 
    [--help] [--source] [--non-interactive] 
    [--api-key] [--force-english-output] [--verbosity] [--config-file]`

## <a name="description"></a>Descrição

O comando `dotnet nuget delete` exclui ou retira da lista um pacote do servidor. Para NuGet.org, a ação é remover o pacote da lista.

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-s|--source <SOURCE>`

Especifica a URL do servidor. URLs com suporte para nuget.org incluem `http://www.nuget.org`, `http://www.nuget.org/api/v3` e `http://www.nuget.org/api/v2/package`. Para feeds privados, substitua o nome do host (por exemplo, `%hostname%/api/v3`).

`--non-interactive`

Não solicita entrada do usuário ou confirmações.

`-k|--api-key <API_KEY>`

A chave da API para o servidor.

`--force-english-output`

Faz com que a saída de linha de comando esteja em inglês.

`--verbosity <LEVEL>`

Exibe essa quantidade de detalhes na saída. O nível pode ser `normal`, `quiet` ou `detailed`.

`--config-file <FILE>`

Um arquivo de configuração do NuGet usado especificamente para esse comando, substituindo outros arquivos de configuração localizados pela descoberta de arquivo de configuração padrão e o processo de encadeamento. O caminho pode ser absoluto ou relativo.
Para obter mais informações sobre arquivos de configuração, consulte [Configurando o comportamento do NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemplos

Exclui a versão 1.0 do pacote MyPackage:

`dotnet nuget delete MyPackage 1.0` 

Exclui a versão 1.0 do pacote MyPackage, não solicita ao usuário credenciais ou outra entrada:

`dotnet nuget delete MyPackage 1.0 --non-interactive`

Exclui a versão 1.0 do pacote MyPackage, especificando um arquivo de configuração personalizado *./config/My.Config*:

`dotnet nuget delete MyPackage 1.0 --config-file ./config/My.Config`

Exclui a versão 1.0 do pacote MyPackage, com detalhamento máximo:

`dotnet nuget delete MyPackage 1.0 --verbosity detailed`

