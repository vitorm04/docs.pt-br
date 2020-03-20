---
title: Função GetCurrentApartmentType (referência a API não gerenciada)
description: A função GetCurrentApartmentType recupera o tipo de apartamento em que o chamador está executando.
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
ms.openlocfilehash: 3fc88f7997ee5a6c25359243e1ee97a041050eb7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176819"
---
# <a name="getcurrentapartmenttype-function"></a><span data-ttu-id="89381-103">Função GetCurrentApartmentType</span><span class="sxs-lookup"><span data-stu-id="89381-103">GetCurrentApartmentType function</span></span>
<span data-ttu-id="89381-104">Recupera o tipo de apartment no qual o chamador está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="89381-104">Retrieves the type of apartment in which the caller is executing.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="89381-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89381-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentApartmentType (
   [in] int                   vFunc,
   [in] IComThreadingInfo*    ptr,
   [out] APTTYPE*             aptType
);
```  

## <a name="parameters"></a><span data-ttu-id="89381-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="89381-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="89381-107">[em] Este parâmetro não é usado.</span><span class="sxs-lookup"><span data-stu-id="89381-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="89381-108">[em] Um ponteiro para uma instância [IComThreadingInfo.](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo)</span><span class="sxs-lookup"><span data-stu-id="89381-108">[in] A pointer to an [IComThreadingInfo](/windows/desktop/api/objidlbase/nn-objidlbase-icomthreadinginfo) instance.</span></span>

`aptType`  
<span data-ttu-id="89381-109">[fora] Um ponteiro para um valor de enumeração [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) que indica o apartamento do chamador.</span><span class="sxs-lookup"><span data-stu-id="89381-109">[out] A pointer to an [APTTYPE](/windows/win32/api/objidlbase/ne-objidlbase-apttype) enumeration value that indicates the caller's apartment.</span></span>

## <a name="return-value"></a><span data-ttu-id="89381-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="89381-110">Return value</span></span>

|<span data-ttu-id="89381-111">Constante</span><span class="sxs-lookup"><span data-stu-id="89381-111">Constant</span></span>  |<span data-ttu-id="89381-112">Valor</span><span class="sxs-lookup"><span data-stu-id="89381-112">Value</span></span>  |<span data-ttu-id="89381-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="89381-113">Description</span></span>  |
|---------|---------|---------|
| `S_OK` | <span data-ttu-id="89381-114">0</span><span class="sxs-lookup"><span data-stu-id="89381-114">0</span></span> | <span data-ttu-id="89381-115">A função foi concluída com sucesso.</span><span class="sxs-lookup"><span data-stu-id="89381-115">The function completed successfully.</span></span> |
| `E_FAIL` | <span data-ttu-id="89381-116">0x80000008</span><span class="sxs-lookup"><span data-stu-id="89381-116">0x80000008</span></span> | <span data-ttu-id="89381-117">O interlocutor não está executando em um apartamento.</span><span class="sxs-lookup"><span data-stu-id="89381-117">The caller is not executing in an apartment.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="89381-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="89381-118">Remarks</span></span>

<span data-ttu-id="89381-119">Esta função envolve uma chamada para o método [IComThreadingInfo::GetCurrentApartmentType.](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype)</span><span class="sxs-lookup"><span data-stu-id="89381-119">This function wraps a call to the [IComThreadingInfo::GetCurrentApartmentType](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="89381-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89381-120">Requirements</span></span>  
 <span data-ttu-id="89381-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89381-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89381-122">**Cabeçalho:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="89381-122">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="89381-123">**.NET Framework Versions:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="89381-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89381-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="89381-124">See also</span></span>

- [<span data-ttu-id="89381-125">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="89381-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
