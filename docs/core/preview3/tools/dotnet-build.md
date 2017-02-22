---
title: Comando dotnet-build | Microsoft Docs
description: "O comando dotnet-build compila um projeto e todas as suas dependências."
keywords: dotnet-build, CLI, comando de CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e1a2bc4-a919-4a86-8f33-a9b218b1fcb3
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: c2c0ae3711c866268c4e8c066b4213e110e771b9

---

#<a name="dotnet-build-net-core-tools-rc4"></a>dotnet-build (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [dotnet-build](../../tools/dotnet-build.md).

## <a name="name"></a>Nome 
dotnet-build – Compila um projeto e todas as suas dependências 

## <a name="synopsis"></a>Sinopse

`dotnet build [--help] [--output]  [--framework]  
    [--configuration]  [--runtime] [--version-suffix]
    [--build-profile]  [--no-incremental] [--no-dependencies]
    [<project>]`

## <a name="description"></a>Descrição

O comando `dotnet build` cria vários arquivos de origem de um projeto de origem e suas dependências em um binário. Por padrão, o binário resultante está em IL (linguagem intermediária) e tem uma extensão DLL. 
`dotnet build` também remove um arquivo `*.deps` que descreve o que o host precisa para executar o aplicativo.  

Compilar requer a existência de um arquivo de ativo (um arquivo que lista todas as dependências do aplicativo), o que significa que é necessário executar [`dotnet restore`](dotnet-restore.md) antes de compilar o código.

Antes de começa qualquer compilação, o verbo `build` analisa o projeto e suas dependências em verificações de segurança incremental.
Se todas as verificações forem aprovadas, o build prossegue incrementalmente no projeto e suas dependências, caso contrário, ela retorna à compilação não incremental. Por meio de um sinalizador de perfil, os usuários podem escolher receber informações adicionais sobre como melhorar o tempo de build.

Para compilar um aplicativo executável em vez de uma biblioteca, é necessário definir a propriedade `<OutputType>`:

```xml
<PropertyGroup>
    <OutputType>Exe</OutputType>
</PropertyGroup>
```

## <a name="options"></a>Opções

`-h|--help`

Imprime uma ajuda breve para o comando.  

`-o|--output <OUTPUT_DIRECTORY>`

Diretório no qual os binários compilados são colocados. Você também precisa definir `--framework` ao especificar essa opção.

`-f|--framework <FRAMEWORK>`

Compila para uma estrutura específica. A estrutura precisa ser definida no [arquivo de projeto](csproj.md).

`-c|--configuration [Debug|Release]`

Define uma configuração de build.  Se omitido, o padrão é `Debug`.

`-r|--runtime [RUNTIME_IDENTIFIER]`

Tempo de execução de destino para a compilação. Para obter uma lista de RIDs (Identificadores de Tempo de Execução) que podem ser usados, consulte o [Catálogo de RIDs](../../rid-catalog.md). 

`--version-suffix [VERSION_SUFFIX]`

Define qual `*` deve ser substituído no campo de versão no arquivo de projeto. O formato segue as diretrizes de versão do NuGet. 

`--build-profile`

Imprime as verificações de segurança incrementais que os usuários precisam resolver para a compilação incremental ser ativada automaticamente.

`--no-incremental`

Marca o build como não segura para build incremental. Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.

`--no-dependencies`

Ignora as referências projeto a projeto e só compila o projeto raiz especificado para build.

## <a name="examples"></a>Exemplos

Compile um projeto e suas dependências:

`dotnet build`

Compile um projeto e suas dependências usando a configuração da Versão:

`dotnet build --configuration Release`

Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`



<!--HONumber=Feb17_HO2-->


