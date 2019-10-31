---
title: Função GetCurrentApartmentType (referência de API não gerenciada)
description: A função GetCurrentApartmentType recupera o tipo de apartamento no qual o chamador está sendo executado.
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
ms.openlocfilehash: 6ecd2b49d6850a8fae25ddca54f855fdda2ccabb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120349"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="fe0dc-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="fe0dc-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="fe0dc-104">Recupera o tipo de apartment no qual o chamador está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="fe0dc-104">Retrieves the type of apartment in which the caller is executing.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="fe0dc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe0dc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc, 
   [in] IComThreadingInfo*    ptr, 
   [out] APTTYPE*             aptType
); 
```  

## <a name="parameters"></a><span data-ttu-id="fe0dc-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe0dc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="fe0dc-107">no Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="fe0dc-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="fe0dc-108">no Um ponteiro para uma instância de [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) .</span><span class="sxs-lookup"><span data-stu-id="fe0dc-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="fe0dc-109">fora Um ponteiro para um valor de enumeração [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) que indica o apartamento do chamador.</span><span class="sxs-lookup"><span data-stu-id="fe0dc-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="fe0dc-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fe0dc-110">Return value</span></span>

|<span data-ttu-id="fe0dc-111">Constante</span><span class="sxs-lookup"><span data-stu-id="fe0dc-111">Constant</span></span>  |<span data-ttu-id="fe0dc-112">Valor</span><span class="sxs-lookup"><span data-stu-id="fe0dc-112">Value</span></span>  |<span data-ttu-id="fe0dc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe0dc-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="fe0dc-114">0</span><span class="sxs-lookup"><span data-stu-id="fe0dc-114">0</span></span> | <span data-ttu-id="fe0dc-115">A função foi concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="fe0dc-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="fe0dc-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="fe0dc-116">0x80000008</span></span> | <span data-ttu-id="fe0dc-117">O chamador não está sendo executado em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="fe0dc-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="fe0dc-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe0dc-118">Remarks</span></span>

<span data-ttu-id="fe0dc-119">Essa função encapsula uma chamada para o método [IComThreadingInfo:: GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="fe0dc-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe0dc-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe0dc-120">Requirements</span></span>  
 <span data-ttu-id="fe0dc-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe0dc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe0dc-122">**Cabeçalho:** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="fe0dc-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="fe0dc-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="fe0dc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0dc-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe0dc-124">See also</span></span>

- [<span data-ttu-id="fe0dc-125">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="fe0dc-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
