---
title: 'NETSDK1022: itens duplicados foram incluídos.'
description: Como resolver a mensagem de item duplicada com base em inclusões padrão.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: bc803f5316bf09c12c563f1a63b8385d1be4e9ce
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506630"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022: itens duplicados foram incluídos.

**Este artigo aplica-se a:** ✔️ o SDK do .NET 2.1.100 e versões posteriores

A partir do Visual Studio 2017/MSBuild versão 15,3, o SDK do .NET inclui automaticamente itens do diretório do projeto por padrão.  Isso inclui `Compile` `Content` destinos e.  Isso deve limpar muito o arquivo do projeto e reduzir a complexidade que você tem.

Você pode reverter para o comportamento anterior definindo a propriedade correta como false.

Exemplo de `Compile` itens:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
