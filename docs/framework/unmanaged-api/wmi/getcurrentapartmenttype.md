---
title: Função GetCurrentApartmentType (referência de API não gerenciada)
description: A função GetCurrentApartmentType recupera o tipo do compartimento em que o chamador está em execução.
ms.date: 11/06/2017
api_name:
- GetCurrentApartmentType
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetCurrentApartmentType
helpviewer_keywords:
- GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca7b5fa5bf6d845d542d3e80c0571e59f3d4c1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461718"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="98ce7-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="98ce7-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="98ce7-104">Recupera o tipo do compartimento em que o chamador está em execução.</span><span class="sxs-lookup"><span data-stu-id="98ce7-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="98ce7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98ce7-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="98ce7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="98ce7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98ce7-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="98ce7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98ce7-108">[in] Um ponteiro para um [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="98ce7-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="98ce7-109">[out] Um ponteiro para um [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) valor de enumeração que indica o compartimento do chamador.</span><span class="sxs-lookup"><span data-stu-id="98ce7-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="98ce7-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="98ce7-110">Return value</span></span>


|<span data-ttu-id="98ce7-111">Constante</span><span class="sxs-lookup"><span data-stu-id="98ce7-111">Constant</span></span>  |<span data-ttu-id="98ce7-112">Valor</span><span class="sxs-lookup"><span data-stu-id="98ce7-112">Value</span></span>  |<span data-ttu-id="98ce7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="98ce7-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="98ce7-114">0</span><span class="sxs-lookup"><span data-stu-id="98ce7-114">0</span></span> | <span data-ttu-id="98ce7-115">A função foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="98ce7-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="98ce7-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="98ce7-116">0x80000008</span></span> | <span data-ttu-id="98ce7-117">O chamador não está em execução em um apartment.</span><span class="sxs-lookup"><span data-stu-id="98ce7-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="98ce7-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="98ce7-118">Remarks</span></span>

<span data-ttu-id="98ce7-119">Essa função encapsula uma chamada para o [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="98ce7-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="98ce7-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="98ce7-120">Requirements</span></span>  
 <span data-ttu-id="98ce7-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98ce7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98ce7-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="98ce7-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98ce7-123">**Versões do .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98ce7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ce7-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98ce7-124">See also</span></span>  
[<span data-ttu-id="98ce7-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="98ce7-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
