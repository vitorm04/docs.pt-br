---
title: Referência global.json
description: Veja o esquema para o arquivo global.json, que permite a definição da versão de ferramentas do .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209964"
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
