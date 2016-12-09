---
title: "Referência global.json | .NET Core"
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
ms.sourcegitcommit: 6f3a46284bd5820520739577919fa202f5b784d7
ms.openlocfilehash: adce52849247f5b12d43b389a7699de04fe278c4

---

# <a name="globaljson-reference"></a>Referência global.json

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



<!--HONumber=Nov16_HO4-->


