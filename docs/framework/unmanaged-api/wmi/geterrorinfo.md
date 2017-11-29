---
title: "Função GetErrorInfo (referência de API não gerenciada)"
description: "A função GetErrorInfo recupera informações de erro na chamada de função anterior."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetErrorInfo
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetErrorInfo
helpviewer_keywords: GetErrorInfo function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1bdaa72723855c6688a7c8c7704b958f6196dfd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="13659-103">Função GetErrorInfo</span><span class="sxs-lookup"><span data-stu-id="13659-103">GetErrorInfo function</span></span>
<span data-ttu-id="13659-104">Recupera informações de erro na chamada de função anterior.</span><span class="sxs-lookup"><span data-stu-id="13659-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="13659-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13659-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="13659-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="13659-106">Return value</span></span>

<span data-ttu-id="13659-107">Um ponteiro para um [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) objeto se a chamada de função for bem-sucedida, ou `null` se ele falhar.</span><span class="sxs-lookup"><span data-stu-id="13659-107">An pointer to an [IErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms221233(v=vs.85).aspx) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="13659-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="13659-108">Remarks</span></span>

<span data-ttu-id="13659-109">Essa função encapsula uma chamada para o [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="13659-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="13659-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13659-110">Requirements</span></span>  
 <span data-ttu-id="13659-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13659-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13659-112">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="13659-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="13659-113">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="13659-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13659-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13659-114">See also</span></span>  
[<span data-ttu-id="13659-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="13659-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
