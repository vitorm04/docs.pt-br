---
title: 'NETSDK1022: itens duplicados foram incluídos.'
description: Como resolver a mensagem de item duplicada com base em inclusões padrão.
author: marcpopMSFT
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1022
ms.openlocfilehash: 46c3d7d451e7c9e5b456b6e4e45054c3a4844386
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445745"
---
# <a name="netsdk1022-duplicate-items-were-included"></a>NETSDK1022: itens duplicados foram incluídos.

**Este artigo aplica-se a:** ✔️ o SDK do .NET 2.1.100 e versões posteriores

A partir do Visual Studio 15,3, o SDK do .NET inclui automaticamente itens do diretório do projeto por padrão.  Isso inclui `Compile` `Content` destinos e.  Isso deve limpar muito o arquivo do projeto e reduzir a complexidade que você tem.

Você pode reverter para o comportamento anterior definindo a propriedade correta como false.

Exemplo de `Compile` itens:

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
