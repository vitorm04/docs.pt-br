---
title: Comando dotnet-publish | Microsoft Docs
description: "O comando dotnet-publish publica seu projeto .NET Core em um diretório."
keywords: dotnet-publish, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 03/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 78487673d8fa07286605fb806f30083747b17386
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Nome

`dotnet-publish` – Empacota o aplicativo e todas as suas dependências em uma pasta, preparando-o para publicação.

## <a name="synopsis"></a>Sinopse

```
dotnet publish [project] [-f|--framework] [-r|--runtime] [-o|--output] [-c|--configuration] [--version-suffix] [-v|--verbosity]
dotnet publish [-h|--help]
```

## <a name="description"></a>Descrição

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório. A saída conterá o seguinte:

1. Código IL (Linguagem Intermediária) em um assembly com uma extensão `*.dll`.
2. Arquivo *deps.json* que contém todas as dependências do projeto. 
3. Arquivo *Runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).
4. Todas as dependências do aplicativo. Elas são copiadas do cache NuGet para a pasta de saída. 

A saída do comando `dotnet publish` está pronta para ser implantada em um computador remoto para execução e é a única forma oficialmente com suporte para preparar o aplicativo para ser implantado em outro computador (por exemplo, um servidor) para execução. Dependendo do tipo de implantação especificado pelo projeto, o computador remoto precisará ter o tempo de execução compartilhado do .NET Core instalado. Para obter mais informações, consulte o tópico [Implantação de Aplicativos .NET Core](../deploying/index.md).

## <a name="arguments"></a>Arguments

`project` 

O projeto a ser publicado, cujo padrão retorna para o diretório atual se `project` não for especificado. 

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-f|--framework <FRAMEWORK>`

Publica o aplicativo para a estrutura de destino especificada. A estrutura de destino deve ser especificada no arquivo de projeto.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publica o aplicativo para um determinado tempo de execução. Isso é usado ao criar uma [implantação independente](../deploying/index.md#self-contained-deployments-scd). Para obter uma lista de RIDs (Identificadores de Tempo de Execução) que podem ser usados, consulte o [Catálogo de RIDs](../rid-catalog.md). O padrão é publicar um [aplicativo dependente de estrutura](../deploying/index.md#framework-dependent-deployments-fdd).

`-o|--output <OUTPUT_PATH>`

Especifique o caminho em que o diretório será colocado. Se não for especificado, o padrão será a *_./bin/[configuração]/[estrutura]/_* para aplicativos portáteis ou *_./bin/[configuração]/[estrutura]/[tempo de execução]_* para implantações autocontidas.

`-c|--configuration {Debug|Release}`

Configuração a ser usada ao compilar o projeto. O valor padrão é `Debug`.

`--version-suffix <VERSION_SUFFIX>`

Define qual `*` deve ser substituído no campo de versão no arquivo de projeto.

`-v|--verbosity <LEVEL>`

Define o nível de detalhes do comando. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.

## <a name="examples"></a>Exemplos

Publicar o projeto encontrado no diretório atual:

`dotnet publish`

Publicar o aplicativo usando o arquivo de projeto especificado:

`dotnet publish ~/projects/app1/app1.csproj`
    
Publicar o projeto encontrado no diretório atual usando a estrutura `netcoreapp1.1`:

`dotnet publish --framework netcoreapp1.1`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (este RID deve existir no arquivo de projeto).

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a>Consulte também
* [Estruturas](../../standard/frameworks.md)
* [Catálogo de RID (Identificador de Tempo de Execução)](../rid-catalog.md)
