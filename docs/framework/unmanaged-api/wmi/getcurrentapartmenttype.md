---
title: "Função GetCurrentApartmentType (referência de API não gerenciada)"
description: "A função GetCurrentApartmentType recupera o tipo do compartimento em que o chamador está em execução."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetCurrentApartmentType
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetCurrentApartmentType
helpviewer_keywords: GetCurrentApartmentType function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b250913b55ba59261a666760cc15466b6f9d096e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="b8304-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="b8304-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="b8304-104">Recupera o tipo do compartimento em que o chamador está em execução.</span><span class="sxs-lookup"><span data-stu-id="b8304-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b8304-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8304-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="b8304-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8304-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b8304-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="b8304-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b8304-108">[in] Um ponteiro para um [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instância.</span><span class="sxs-lookup"><span data-stu-id="b8304-108">[in] A pointer to an [IComThreadingInfo](https://msdn.microsoft.com/library/windows/desktop/ms694502(v=vs.85).aspx) instance.</span></span>

`aptType`  
<span data-ttu-id="b8304-109">[out] Um ponteiro para um [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) valor de enumeração que indica o compartimento do chamador.</span><span class="sxs-lookup"><span data-stu-id="b8304-109">[out] A pointer to an [APTTYPE](https://msdn.microsoft.com/library/windows/desktop/ms693793(v=vs.85).aspx) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="b8304-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8304-110">Return value</span></span>


|<span data-ttu-id="b8304-111">Constante</span><span class="sxs-lookup"><span data-stu-id="b8304-111">Constant</span></span>  |<span data-ttu-id="b8304-112">Valor</span><span class="sxs-lookup"><span data-stu-id="b8304-112">Value</span></span>  |<span data-ttu-id="b8304-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8304-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="b8304-114">0</span><span class="sxs-lookup"><span data-stu-id="b8304-114">0</span></span> | <span data-ttu-id="b8304-115">A função foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="b8304-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="b8304-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="b8304-116">0x80000008</span></span> | <span data-ttu-id="b8304-117">O chamador não está em execução em um apartment.</span><span class="sxs-lookup"><span data-stu-id="b8304-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="b8304-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8304-118">Remarks</span></span>

<span data-ttu-id="b8304-119">Essa função encapsula uma chamada para o [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) método.</span><span class="sxs-lookup"><span data-stu-id="b8304-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](https://msdn.microsoft.com/library/windows/desktop/ms683752(v=vs.85).aspx) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8304-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8304-120">Requirements</span></span>  
 <span data-ttu-id="b8304-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8304-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8304-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b8304-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b8304-123">**Versões do .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8304-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8304-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8304-124">See also</span></span>  
[<span data-ttu-id="b8304-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b8304-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
