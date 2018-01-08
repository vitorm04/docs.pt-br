---
title: "Referência global.json"
description: "Veja o esquema para o arquivo global.json, que permite a definição da versão de ferramentas do .NET Core."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="b45ed-104">Referência global.json</span><span class="sxs-lookup"><span data-stu-id="b45ed-104">global.json reference</span></span>

<span data-ttu-id="b45ed-105">O arquivo *global.json* permite a seleção da versão das ferramentas do .NET Core usada por meio da propriedade `sdk`.</span><span class="sxs-lookup"><span data-stu-id="b45ed-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="b45ed-106">As ferramentas da CLI do .NET Core procuram esse arquivo no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="b45ed-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="b45ed-107">sdk</span><span class="sxs-lookup"><span data-stu-id="b45ed-107">sdk</span></span>
<span data-ttu-id="b45ed-108">Tipo: Object</span><span class="sxs-lookup"><span data-stu-id="b45ed-108">Type: Object</span></span>

<span data-ttu-id="b45ed-109">Especifica informações sobre o SDK.</span><span class="sxs-lookup"><span data-stu-id="b45ed-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="b45ed-110">version</span><span class="sxs-lookup"><span data-stu-id="b45ed-110">version</span></span>
<span data-ttu-id="b45ed-111">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="b45ed-111">Type: String</span></span>

<span data-ttu-id="b45ed-112">A versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="b45ed-112">The version of the SDK to use.</span></span>

<span data-ttu-id="b45ed-113">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b45ed-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
