---
title: "Referência global.json | Microsoft Docs"
description: "Referência global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.translationtype: Human Translation
ms.sourcegitcommit: ec7028d43e7236056e5a53160f6017edadfec8c2
ms.openlocfilehash: a35938d355cb86205e9c822736862298508cf861
ms.contentlocale: pt-br
ms.lasthandoff: 04/06/2017

---

# <a name="globaljson-reference"></a>Referência global.json

O arquivo *global.json* permite a seleção da versão das ferramentas do .NET Core usada por meio da propriedade `sdk`.

As ferramentas da CLI do .NET Core procuram esse arquivo no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.

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

