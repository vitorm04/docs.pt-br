---
title: "Referência global.json | .NET Core"
description: "Referência global.json"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 281f1b717a0e220e533078e973711977617a1401

---

# <a name="globaljson-reference"></a>Referência global.json

O arquivo global.json ainda está presente na Linha de Comando da Visualização 3 do .NET Core. No entanto, sua finalidade principal não é definir metadados de solução, como nas versões anteriores, mas permitir a seleção da versão da CLI que está sendo usado por meio da propriedade `sdk`. 

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



<!--HONumber=Nov16_HO3-->


