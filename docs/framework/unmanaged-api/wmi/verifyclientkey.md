---
title: "Função VerifyClientKey (referência de API não gerenciada)"
description: "A função VerifyClientKey garante que a chave do cliente tem a segurança correta."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: VerifyClientKey
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: VerifyClientKey
helpviewer_keywords: VerifyClientKey function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ada878ff8bc430ab2a2d48cac13a81b1f64d39f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="1b163-103">Função VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="1b163-103">VerifyClientKey function</span></span>
<span data-ttu-id="1b163-104">Garante que a chave do cliente tem a segurança correta.</span><span class="sxs-lookup"><span data-stu-id="1b163-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1b163-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b163-105">Syntax</span></span>  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="1b163-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1b163-106">Return value</span></span>

<span data-ttu-id="1b163-107">Se a função tiver êxito, o valor de retorno é `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="1b163-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="1b163-108">Se a função falhar, o valor de retorno é um código de erro diferente de zero definido em *Winerror. H*.</span><span class="sxs-lookup"><span data-stu-id="1b163-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b163-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b163-109">Requirements</span></span>  
 <span data-ttu-id="1b163-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b163-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b163-111">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="1b163-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="1b163-112">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1b163-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b163-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b163-113">See also</span></span>  
[<span data-ttu-id="1b163-114">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1b163-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
