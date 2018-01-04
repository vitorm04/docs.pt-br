---
title: "Inicializar a função (referência de API não gerenciada)"
description: "A função Initialize executa a inicialização do WMI."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: Initialize
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: Initialize
helpviewer_keywords: Initialize function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d62d959c5dfeac237abb20b86df87ae07a077dbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="initialize-function"></a><span data-ttu-id="9bd50-103">Função Initialize</span><span class="sxs-lookup"><span data-stu-id="9bd50-103">Initialize function</span></span>
<span data-ttu-id="9bd50-104">Executa a inicialização do WMI.</span><span class="sxs-lookup"><span data-stu-id="9bd50-104">Performs WMI initialization.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9bd50-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd50-105">Syntax</span></span> 
```  
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
); 
```  
## <a name="parameters"></a><span data-ttu-id="9bd50-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9bd50-106">Parameters</span></span>

`bAllowIManagementObjectQI`   
<span data-ttu-id="9bd50-107">[in] `true` para indicar que são permitidas chamadas de QueryInterface em objetos do WMI; `false` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="9bd50-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bd50-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9bd50-108">Return value</span></span>

<span data-ttu-id="9bd50-109">A função sempre retorna `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="9bd50-109">The function always returns `S_OK` (0).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9bd50-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9bd50-110">Requirements</span></span>  
 <span data-ttu-id="9bd50-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bd50-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bd50-112">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="9bd50-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="9bd50-113">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9bd50-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd50-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd50-114">See also</span></span>  
[<span data-ttu-id="9bd50-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="9bd50-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
