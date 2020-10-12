---
title: 'NETSDK1005 e NETSDK1047: o arquivo de ativo está com destino ausente'
description: Como resolver o problema de um arquivo de ativo que não tem um destino.
author: sfoslund
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1005
- NETSDK1047
ms.openlocfilehash: 6c22fd8c79c2ac6e024b46b4f67e08011d42efc6
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957134"
---
# <a name="netsdk1005-and-netsdk1047-asset-file-is-missing-target"></a><span data-ttu-id="20090-103">NETSDK1005 e NETSDK1047: o arquivo de ativo está com destino ausente</span><span class="sxs-lookup"><span data-stu-id="20090-103">NETSDK1005 and NETSDK1047: Asset file is missing target</span></span>

<span data-ttu-id="20090-104">**Este artigo aplica-se a:** ✔️ o SDK do .NET 2.1.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="20090-104">**This article applies to:** ✔️ .NET 2.1.100 SDK and later versions</span></span>

<span data-ttu-id="20090-105">Quando o SDK do .NET emite o erro NETSDK1005 ou NETSDK1047, o arquivo de ativos do projeto não tem informações sobre uma de suas estruturas de destino.</span><span class="sxs-lookup"><span data-stu-id="20090-105">When the .NET SDK issues error NETSDK1005 or NETSDK1047, the project's assets file is missing information on one of your target frameworks.</span></span> <span data-ttu-id="20090-106">Normalmente, isso pode ser corrigido garantindo que a restauração seja executada e que o valor de destino ausente seja incluído na `TargetFrameworks` Propriedade do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="20090-106">This can usually be fixed by ensuring that restore is run and that the missing target value is included in the `TargetFrameworks` property of your project.</span></span>

> [!NOTE]
> <span data-ttu-id="20090-107">Houve um problema conhecido com as primeiras compilações do .NET 5 Preview 8 quando usadas com versões do Visual Studio 16,8 visualizações que resultaram nesse erro.</span><span class="sxs-lookup"><span data-stu-id="20090-107">There was a known issue with early builds of .NET 5 preview 8 when used with versions of Visual Studio 16.8 previews which resulted in this error.</span></span> <span data-ttu-id="20090-108">Especificamente, se o destino ausente for `net5.0-windows7.0` ou `net5.0` , verifique se você atualizou para as versões mais recentes do Visual Studio e do SDK do .NET 5.</span><span class="sxs-lookup"><span data-stu-id="20090-108">Specifically, if the missing target is `net5.0-windows7.0` or `net5.0`, ensure that you have updated to the latest versions of Visual Studio and the .NET 5 SDK.</span></span>
