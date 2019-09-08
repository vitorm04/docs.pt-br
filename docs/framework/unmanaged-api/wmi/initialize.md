---
title: Inicializar função (referência de API não gerenciada)
description: A função Initialize executa a inicialização do WMI.
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
ms.openlocfilehash: 1bc3688b30180bdcde0a87027955a789de749f90
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798432"
---
# <a name="initialize-function"></a><span data-ttu-id="88e5d-103">Inicializar função</span><span class="sxs-lookup"><span data-stu-id="88e5d-103">Initialize function</span></span>

<span data-ttu-id="88e5d-104">Executa a inicialização do WMI.</span><span class="sxs-lookup"><span data-stu-id="88e5d-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="88e5d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88e5d-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="88e5d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88e5d-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="88e5d-107">no `true` para indicar que as chamadas para QueryInterface em objetos WMI são permitidas; `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="88e5d-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="88e5d-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="88e5d-108">Return value</span></span>

<span data-ttu-id="88e5d-109">A função sempre retorna `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="88e5d-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="88e5d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88e5d-110">Requirements</span></span>

<span data-ttu-id="88e5d-111">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88e5d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="88e5d-112">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="88e5d-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="88e5d-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88e5d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="88e5d-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e5d-114">See also</span></span>

- [<span data-ttu-id="88e5d-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="88e5d-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
