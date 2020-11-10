---
title: 'NETSDK1013: o valor de TargetFramework não foi reconhecido.'
description: Como determinar e definir um valor de TargetFramework válido
author: marcpop
ms.topic: error-reference
ms.date: 10/9/2020
f1_keywords:
- NETSDK1013
ms.openlocfilehash: bcaed878b663f8bc957e8469ffd78caa9babf710
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445741"
---
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a>NETSDK1013: o valor de TargetFramework não foi reconhecido

**Este artigo aplica-se a:** ✔️ o SDK do .net 3.1.100 e versões posteriores

O SDK tenta analisar os valores fornecidos no arquivo de projeto para `<TargetFramework>` ou `<TargetFrameworks>` em um valor bem conhecido.  Se o valor não for reconhecido, o `TargetFrameworkIdentifier` `TargetFrameworkVersion` valor ou poderá ser definido como uma cadeia de caracteres vazia ou `Unsupported` .

Para resolver isso, verifique a ortografia do seu `TargetFramework` valor na lista de [estruturas com suporte](../../../standard/frameworks.md).
Você também pode definir as `TargetFrameworkIdentifier` `TargetFrameworkVersion` Propriedades e diretamente em seu arquivo de projeto.

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
