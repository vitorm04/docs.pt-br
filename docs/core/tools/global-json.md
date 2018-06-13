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
# <a name="globaljson-reference"></a><span data-ttu-id="f41fc-103">Referência global.json</span><span class="sxs-lookup"><span data-stu-id="f41fc-103">global.json reference</span></span>

<span data-ttu-id="f41fc-104">O arquivo *global.json* permite a seleção da versão das ferramentas do .NET Core usada por meio da propriedade `sdk`.</span><span class="sxs-lookup"><span data-stu-id="f41fc-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="f41fc-105">As ferramentas da CLI do .NET Core procuram esse arquivo no diretório de trabalho atual (que não necessariamente é o mesmo que o diretório do projeto) ou um de seus diretórios pai.</span><span class="sxs-lookup"><span data-stu-id="f41fc-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="f41fc-106">sdk</span><span class="sxs-lookup"><span data-stu-id="f41fc-106">sdk</span></span>
<span data-ttu-id="f41fc-107">Tipo: Object</span><span class="sxs-lookup"><span data-stu-id="f41fc-107">Type: Object</span></span>

<span data-ttu-id="f41fc-108">Especifica informações sobre o SDK.</span><span class="sxs-lookup"><span data-stu-id="f41fc-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="f41fc-109">version</span><span class="sxs-lookup"><span data-stu-id="f41fc-109">version</span></span>
<span data-ttu-id="f41fc-110">Tipo: String</span><span class="sxs-lookup"><span data-stu-id="f41fc-110">Type: String</span></span>

<span data-ttu-id="f41fc-111">A versão do SDK a ser usada.</span><span class="sxs-lookup"><span data-stu-id="f41fc-111">The version of the SDK to use.</span></span>

<span data-ttu-id="f41fc-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f41fc-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
