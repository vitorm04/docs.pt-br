---
title: "Referência global.json | Microsoft Docs"
description: "Referência global.json"
keywords: .NET, .NET Core
author: aL3891
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a6b0ad546a8a121ad5ea4642c11842a8dccf7055

---

# <a name="globaljson-reference"></a>Referência global.json

> [!WARNING]
> Este tópico se aplica à Visualização 2 das Ferramentas do .NET Core. Para a versão do Ferramentas do .NET Core RC4, consulte o tópico [Referência global.json (Ferramentas do .NET Core RC4)](../preview3/tools/global-json.md).

O arquivo global.json é usado em projetos do .NET Core para definir os metadados de solução. Esse arquivo é usado quando o comando [dotnet-restore](dotnet-restore.md) é invocado para restaurar as dependências de um projeto do .NET Core.
Neste tópico de referência, a lista de todas as propriedades que podem ser definidas no arquivo project.json será apresentada.

## <a name="projects"></a>projetos
Digite: String[]

Especifica em quais pastas o sistema de build deve pesquisar os projetos ao resolver as dependências. O sistema de build só pesquisará em pastas-filho de nível superior.

Por exemplo:

```json
{
    "projects": [ "src", "test" ]
}
```

## <a name="packages"></a>pacotes
Tipo: String

O local para armazenar pacotes.

Por exemplo:
```json
{
    "packages": "packages-dir"
}
```

## <a name="sdk"></a>sdk
Tipo: Object

Especifica informações sobre o SDK.

### <a name="version"></a>version
Tipo: String

A versão do SDK a ser usada.

Por exemplo:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```



<!--HONumber=Feb17_HO2-->


