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
# <a name="netsdk1013-the-targetframework-value-was-not-recognized"></a><span data-ttu-id="b6fe8-103">NETSDK1013: o valor de TargetFramework não foi reconhecido</span><span class="sxs-lookup"><span data-stu-id="b6fe8-103">NETSDK1013: The TargetFramework value was not recognized</span></span>

<span data-ttu-id="b6fe8-104">**Este artigo aplica-se a:** ✔️ o SDK do .net 3.1.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="b6fe8-104">**This article applies to:** ✔️ .NET 3.1.100 SDK and later versions</span></span>

<span data-ttu-id="b6fe8-105">O SDK tenta analisar os valores fornecidos no arquivo de projeto para `<TargetFramework>` ou `<TargetFrameworks>` em um valor bem conhecido.</span><span class="sxs-lookup"><span data-stu-id="b6fe8-105">The SDK tries to parse the values provided in the project file for `<TargetFramework>` or `<TargetFrameworks>` into a well known value.</span></span>  <span data-ttu-id="b6fe8-106">Se o valor não for reconhecido, o `TargetFrameworkIdentifier` `TargetFrameworkVersion` valor ou poderá ser definido como uma cadeia de caracteres vazia ou `Unsupported` .</span><span class="sxs-lookup"><span data-stu-id="b6fe8-106">If the value is not recognized, the `TargetFrameworkIdentifier` or `TargetFrameworkVersion` value may be set to an empty string or `Unsupported`.</span></span>

<span data-ttu-id="b6fe8-107">Para resolver isso, verifique a ortografia do seu `TargetFramework` valor na lista de [estruturas com suporte](../../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="b6fe8-107">To resolve this, check the spelling of your `TargetFramework` value from the list of [supported frameworks](../../../standard/frameworks.md).</span></span>
<span data-ttu-id="b6fe8-108">Você também pode definir as `TargetFrameworkIdentifier` `TargetFrameworkVersion` Propriedades e diretamente em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b6fe8-108">You can also set the `TargetFrameworkIdentifier` and `TargetFrameworkVersion` properties directly in your project file.</span></span>

```xml
<PropertyGroup Condition="'$(TargetFrameworkIdentifier)' == ''">
  <TargetFrameworkIdentifier>.NETCOREAPP</TargetFrameworkIdentifier>
  <TargetFrameworkVersion>3.1</TargetFrameworkVersion>
</PropertyGroup>
```
