---
title: Comando dotnet-publish | SDK do .NET Core
description: "O comando dotnet-publish publica seu projeto .NET Core em um diretório."
keywords: dotnet-publish, CLI, comando da CLI, .NET Core
author: mairaw
manager: wpickett
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: e480c32faa22859de74e06f3a199fba1c0720c46

---

#<a name="dotnet-publish"></a>dotnet-publish

## <a name="name"></a>Nome

`dotnet-publish` – Empacota o aplicativo e todas as suas dependências em uma pasta, preparando-o para publicação

## <a name="synopsis"></a>Sinopse

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--output]  
    [--version-suffix] [--configuration]`

## <a name="description"></a>Descrição

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório. 

Dependendo do tipo de aplicativo portátil, o diretório resultante conterá o seguinte:

1. *Implantação dependente de estrutura* – O código de IL (linguagem intermediária) do aplicativo e todas as dependências gerenciadas do aplicativo.
2. *Implantação autocontida* – O mesmo citado acima, mais todo o tempo de execução para a plataforma de destino.

Para obter mais informações, consulte o tópico [Implantação de Aplicativos .NET Core](../deploying/index.md).

## <a name="options"></a>Opções

`[project]` 

O projeto a ser publicado, cujo padrão retorna para o diretório atual se `[project]` não for especificado. 

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-f|--framework <FRAMEWORK>`

Publica o aplicativo para um determinado FID (Identificador de Estrutura). 

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publica o aplicativo para um determinado tempo de execução. Para obter uma lista de RIDs (Identificadores de Tempo de Execução) que podem ser usados, consulte o [Catálogo de RIDs](../../rid-catalog.md).

`-o|--output <OUTPUT_PATH>`

Especifique o caminho em que o diretório será colocado. Se não for especificado, o padrão será a *_./bin/[configuração]/[estrutura]/_* para aplicativos portáteis ou *_./bin/[configuração]/[estrutura]/[tempo de execução]_* para implantações autocontidas.

`--version-suffix [VERSION_SUFFIX]`

Define qual `*` deve ser substituído no campo de versão no arquivo de projeto.

`-c|--configuration [Debug|Release]`

Configuração a ser usada durante a publicação. O valor padrão é `Debug`.

## <a name="examples"></a>Exemplos

Publique um aplicativo.

`dotnet publish`

Publique o aplicativo usando o arquivo de projeto especificado

`dotnet publish ~/projects/app1/app1.csproj`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.0`:

`dotnet publish --framework netcoreapp1.0`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.0` e o tempo de execução para `OS X 10.10` (este RID deve existir no arquivo de projeto).

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>Consulte também
* [Estruturas](../../../standard/frameworks.md)
* [Catálogo de RID (Identificador de Tempo de Execução)](../../rid-catalog.md)



<!--HONumber=Nov16_HO3-->


