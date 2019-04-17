---
title: Inicializar a função (referência de API não gerenciada)
description: A função Initialize executa a inicialização de WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c71b2b6d6f102d19d30d480ee9bafcac3c204be
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611075"
---
# <a name="initialize-function"></a><span data-ttu-id="cd78d-103">Função Initialize</span><span class="sxs-lookup"><span data-stu-id="cd78d-103">Initialize function</span></span>

<span data-ttu-id="cd78d-104">Executa a inicialização do WMI.</span><span class="sxs-lookup"><span data-stu-id="cd78d-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="cd78d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd78d-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="cd78d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd78d-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="cd78d-107">[in] `true` para indicar que as chamadas para QueryInterface em objetos WMI são permitidas; `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="cd78d-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd78d-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cd78d-108">Return value</span></span>

<span data-ttu-id="cd78d-109">A função sempre retorna `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="cd78d-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="cd78d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd78d-110">Requirements</span></span>

<span data-ttu-id="cd78d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd78d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="cd78d-112">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="cd78d-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="cd78d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cd78d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cd78d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd78d-114">See also</span></span>

- [<span data-ttu-id="cd78d-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="cd78d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
