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
ms.openlocfilehash: 76c852ac81126895ea3a2e1b40473722c8445201
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746562"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="677f2-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="677f2-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="677f2-104">Recupera o tipo de apartment no qual o chamador está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="677f2-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="677f2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="677f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="677f2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="677f2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="677f2-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="677f2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="677f2-108">[in] Um ponteiro para um [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instância.</span><span class="sxs-lookup"><span data-stu-id="677f2-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="677f2-109">[out] Um ponteiro para um [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) valor de enumeração que indica o apartment do chamador.</span><span class="sxs-lookup"><span data-stu-id="677f2-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="677f2-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="677f2-110">Return value</span></span>

|<span data-ttu-id="677f2-111">Constante</span><span class="sxs-lookup"><span data-stu-id="677f2-111">Constant</span></span>  |<span data-ttu-id="677f2-112">Valor</span><span class="sxs-lookup"><span data-stu-id="677f2-112">Value</span></span>  |<span data-ttu-id="677f2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="677f2-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="677f2-114">0</span><span class="sxs-lookup"><span data-stu-id="677f2-114">0</span></span> | <span data-ttu-id="677f2-115">A função foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="677f2-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="677f2-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="677f2-116">0x80000008</span></span> | <span data-ttu-id="677f2-117">O chamador não está em execução em um apartment.</span><span class="sxs-lookup"><span data-stu-id="677f2-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="677f2-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="677f2-118">Remarks</span></span>

<span data-ttu-id="677f2-119">Essa função encapsula uma chamada para o [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) método.</span><span class="sxs-lookup"><span data-stu-id="677f2-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="677f2-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="677f2-120">Requirements</span></span>  
 <span data-ttu-id="677f2-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="677f2-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="677f2-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="677f2-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="677f2-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="677f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="677f2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="677f2-124">See also</span></span>

- [<span data-ttu-id="677f2-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="677f2-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
