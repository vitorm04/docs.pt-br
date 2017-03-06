---
title: Comando dotnet-publish | Microsoft Docs
description: "O comando dotnet-publish publica seu projeto .NET Core em um diretório."
keywords: dotnet-publish, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/07/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 8a7e1c52-5c57-4bf5-abad-727450ebeefd
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: 1cf1611ab83874ad44855521d21040d102206338

---

#<a name="dotnet-publish"></a>dotnet-publish

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a versão do Ferramentas do .NET Core RC4, consulte o tópico [dotnet-publish (Ferramentas do .NET Core RC4)](../preview3/tools/dotnet-publish.md).

## <a name="name"></a>Nome

`dotnet-publish` – Empacota o aplicativo e todas as suas dependências em uma pasta, preparando-o para publicação.

## <a name="synopsis"></a>Sinopse

`dotnet publish [project] 
    [--help] [--framework]  
    [--runtime] [--build-base-path] [--output]  
    [--version-suffix] [--configuration] [--native-subdirectory] [--no-build]`

## <a name="description"></a>Descrição

`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo [project.json](project-json.md) e publica o conjunto de arquivos resultantes em um diretório. 

Dependendo do tipo de aplicativo portátil, o diretório resultante conterá o seguinte:

1. *Aplicativo portátil* – O código de IL (linguagem intermediária) do aplicativo e todas as dependências gerenciadas do aplicativo.
    * *Aplicativos portáteis com dependências nativas* – O mesmo que acima, com um subdiretório para a plataforma com suporte de cada dependência nativa. 
2. *Aplicativo autocontido* – O mesmo que acima, mais todo o tempo de execução para a plataforma de destino.

Para obter mais informações, consulte o tópico [Implantação de Aplicativos .NET Core](../deploying/index.md).

## <a name="options"></a>Opções

`[project]` 

O projeto a ser publicado, cujo padrão retorna para o diretório atual se `[project]` não for especificado. Esse valor pode ser um caminho para o arquivo [project.json](project-json.md) ou para o diretório do projeto que contém o arquivo [project.json](project-json.md). Se nenhum arquivo [project.json](project-json.md) puder ser encontrado, `dotnet publish` gera um erro. 

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-f|--framework <FRAMEWORK>`

Publica o aplicativo para um determinado FID (Identificador de Estrutura). Se não for especificado, o FID é lido da [project.json](project-json.md#frameworks). Se nenhuma estrutura válida for encontrada, o comando gera um erro. Se várias estruturas válidas forem encontradas, o comando publica para todas as estruturas válidas. 

`-r|--runtime <RUNTIME_IDENTIFIER>`

Publica o aplicativo para um determinado tempo de execução. Para obter uma lista de RIDs (Identificadores de Tempo de Execução) que podem ser usados, consulte o [Catálogo de RIDs](../rid-catalog.md).

`-b|--build-base-path <OUTPUT_DIRECTORY>`

Diretório no qual as saídas temporárias são colocadas.

`-o|--output <OUTPUT_PATH>`

Especifique o caminho em que o diretório será colocado. Se não for especificado, o padrão será a *_./bin/[configuração]/[estrutura]/_* para aplicativos portáteis ou *_./bin/[configuração]/[estrutura]/[tempo de execução]_* para implantações autocontidas.

`--version-suffix [VERSION_SUFFIX]`

Define pelo que `*` deve ser substituído no campo de versão no arquivo project.json.

`-c|--configuration [Debug|Release]`

Configuração a ser usada durante a publicação. O valor padrão é `Debug`.

`[--native-subdirectory]` Mecanismo temporário para incluir subdiretórios de ativos nativos de pacotes de dependência na saída. 

`[--no-build]` Não compila projetos antes da publicação.

## <a name="examples"></a>Exemplos

Publique um aplicativo usando a estrutura encontrada em `project.json`. Se `project.json` contiver o nó [tempos de execução](project-json.md#runtimes), publique para o RID da plataforma atual.

`dotnet publish`

Publique o aplicativo usando o [project.json](project-json.md) especificado:

`dotnet publish ~/projects/app1/project.json`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.0`:

`dotnet publish --framework netcoreapp1.0`
    
Publique o aplicativo atual usando a estrutura `netcoreapp1.0` e o tempo de execução para `OS X 10.10` (este RID deve existir no nó [tempos de execução](project-json.md#runtimes) do `project.json`):

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

## <a name="see-also"></a>Consulte também
* [Estruturas](../../standard/frameworks.md)
* [Catálogo de RID (Identificador de Tempo de Execução)](../rid-catalog.md)


<!--HONumber=Feb17_HO2-->


