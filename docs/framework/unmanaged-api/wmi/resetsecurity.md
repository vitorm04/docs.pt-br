---
title: "Função ResetSecurity (referência de API não gerenciada)"
description: "A função ResetSecurity atribui um token de representação para o thread atual."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bacee65633d25e705d978d3902a6804516a88bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="resetsecurity-function"></a><span data-ttu-id="d33af-103">Função ResetSecurity</span><span class="sxs-lookup"><span data-stu-id="d33af-103">ResetSecurity function</span></span>
<span data-ttu-id="d33af-104">Atribui o token de representação fornecido para o thread atual.</span><span class="sxs-lookup"><span data-stu-id="d33af-104">Assigns the supplied impersonation token to the current thread.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d33af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d33af-105">Syntax</span></span>  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a><span data-ttu-id="d33af-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d33af-106">Parameters</span></span>

`token`  
<span data-ttu-id="d33af-107">[in] O token de representação para associar o thread atual.</span><span class="sxs-lookup"><span data-stu-id="d33af-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="d33af-108">Seu valor pode ser `null`.</span><span class="sxs-lookup"><span data-stu-id="d33af-108">Its value can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="d33af-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d33af-109">Return value</span></span>

<span data-ttu-id="d33af-110">Se a função tiver êxito, o valor de retorno é `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="d33af-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="d33af-111">Se a função falhar, o valor de retorno é um código de erro diferente de zero.</span><span class="sxs-lookup"><span data-stu-id="d33af-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="d33af-112">Para obter mais informações sobre o erro, chame o [GetErrorInfo](geterrorinfo.md) função.</span><span class="sxs-lookup"><span data-stu-id="d33af-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="d33af-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d33af-113">Requirements</span></span>  
 <span data-ttu-id="d33af-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d33af-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d33af-115">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d33af-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d33af-116">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d33af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33af-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d33af-117">See also</span></span>  
[<span data-ttu-id="d33af-118">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="d33af-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
