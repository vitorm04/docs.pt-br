---
title: Método ServicePointManager. CloseConnectionGroups (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.CloseConnectionGroups
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: aae9a389ae35e249d43c9dc830a68ec32cf4afef
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990295"
---
# <a name="servicepointmanagercloseconnectiongroups-method"></a><span data-ttu-id="7da8d-102">Método ServicePointManager. CloseConnectionGroups</span><span class="sxs-lookup"><span data-stu-id="7da8d-102">ServicePointManager.CloseConnectionGroups method</span></span>

<span data-ttu-id="7da8d-103">Itera em todos os pontos de serviço e fecha os grupos de conexão que têm o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="7da8d-103">Iterates through all service points and closes connection groups that have the specified name.</span></span>

```csharp
internal static void CloseConnectionGroups(string connectionGroupName)
```

> [!WARNING]
> <span data-ttu-id="7da8d-104">Esse método é interno e não deve ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="7da8d-104">This method is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="7da8d-105">A Microsoft não oferece suporte ao uso desse método em um aplicativo de produção em qualquer circunstância.</span><span class="sxs-lookup"><span data-stu-id="7da8d-105">Microsoft does not support the use of this method in a production application under any circumstance.</span></span>

## <a name="parameters"></a><span data-ttu-id="7da8d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7da8d-106">Parameters</span></span>

<span data-ttu-id="7da8d-107">`connectionGroupName` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="7da8d-107">`connectionGroupName` <xref:System.String></span></span>

<span data-ttu-id="7da8d-108">O nome do grupo de conexões a ser fechado.</span><span class="sxs-lookup"><span data-stu-id="7da8d-108">The name of the connection group to close.</span></span>

## <a name="requirements"></a><span data-ttu-id="7da8d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7da8d-109">Requirements</span></span>

<span data-ttu-id="7da8d-110">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="7da8d-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="7da8d-111">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="7da8d-111">**Assembly:** System (in System.dll)</span></span>
