---
title: "Referência global.json | Microsoft Docs"
description: "Referência global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: b814bfc79c2fcd0fd15b9494c18c6d0443a70fb1

---

# <a name="globaljson-reference-net-core-tools-rc4"></a>Referência global.json (Ferramentas do .NET Core RC4)

> [!WARNING]
> Este tópico se aplica às Ferramentas do .NET Core RC4. Para a versão da Visualização 2 das Ferramentas do .NET Core, consulte o tópico [Referência global.json](../../tools/global-json.md).

O arquivo global.json ainda está presente na Linha de Comando do RC4 do .NET Core. No entanto, sua finalidade principal não é definir metadados de solução, como nas versões anteriores, mas permitir a seleção da versão da CLI que está sendo usado por meio da propriedade `sdk`. 

Esta referência reflete o fato acima. 

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


