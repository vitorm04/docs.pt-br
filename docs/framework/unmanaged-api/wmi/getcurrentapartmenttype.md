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
ms.openlocfilehash: 9ead1c1a91b910e7cfbb09f17ba823fc7a77ce0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609003"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="1671b-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="1671b-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="1671b-104">Recupera o tipo de apartment no qual o chamador está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="1671b-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1671b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1671b-105">Syntax</span></span>  
  
```  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="1671b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1671b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="1671b-107">[in] Esse parâmetro é usado.</span><span class="sxs-lookup"><span data-stu-id="1671b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="1671b-108">[in] Um ponteiro para um [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instância.</span><span class="sxs-lookup"><span data-stu-id="1671b-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="1671b-109">[out] Um ponteiro para um [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) valor de enumeração que indica o apartment do chamador.</span><span class="sxs-lookup"><span data-stu-id="1671b-109">[out] A pointer to an [APTTYPE](/windows/desktop/api/objidlbase/ne-objidlbase-_apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="1671b-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="1671b-110">Return value</span></span>

|<span data-ttu-id="1671b-111">Constante</span><span class="sxs-lookup"><span data-stu-id="1671b-111">Constant</span></span>  |<span data-ttu-id="1671b-112">Valor</span><span class="sxs-lookup"><span data-stu-id="1671b-112">Value</span></span>  |<span data-ttu-id="1671b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="1671b-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="1671b-114">0</span><span class="sxs-lookup"><span data-stu-id="1671b-114">0</span></span> | <span data-ttu-id="1671b-115">A função foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="1671b-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="1671b-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="1671b-116">0x80000008</span></span> | <span data-ttu-id="1671b-117">O chamador não está em execução em um apartment.</span><span class="sxs-lookup"><span data-stu-id="1671b-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="1671b-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="1671b-118">Remarks</span></span>

<span data-ttu-id="1671b-119">Essa função encapsula uma chamada para o [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) método.</span><span class="sxs-lookup"><span data-stu-id="1671b-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1671b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1671b-120">Requirements</span></span>  
 <span data-ttu-id="1671b-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1671b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1671b-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="1671b-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1671b-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1671b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1671b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1671b-124">See also</span></span>

- [<span data-ttu-id="1671b-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="1671b-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
