---
title: Função GetErrorInfo (referência de API não gerenciada)
description: A função GetErrorInfo recupera informações de erro de chamada de função anterior.
ms.date: 11/06/2017
api_name:
- GetErrorInfo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetErrorInfo
helpviewer_keywords:
- GetErrorInfo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b27dae07697943c696dc3419f2414701feb1220
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577666"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b8ecc-103">Função GetErrorInfo</span><span class="sxs-lookup"><span data-stu-id="b8ecc-103">GetErrorInfo function</span></span>
<span data-ttu-id="b8ecc-104">Recupera informações de erro da chamada de função anterior.</span><span class="sxs-lookup"><span data-stu-id="b8ecc-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b8ecc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8ecc-105">Syntax</span></span>  
  
```  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b8ecc-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8ecc-106">Return value</span></span>

<span data-ttu-id="b8ecc-107">Um ponteiro para um [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) objeto se a chamada de função for bem-sucedida, ou `null` se ele falhar.</span><span class="sxs-lookup"><span data-stu-id="b8ecc-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b8ecc-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8ecc-108">Remarks</span></span>

<span data-ttu-id="b8ecc-109">Essa função encapsula uma chamada para o [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) método.</span><span class="sxs-lookup"><span data-stu-id="b8ecc-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b8ecc-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8ecc-110">Requirements</span></span>  
 <span data-ttu-id="b8ecc-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8ecc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ecc-112">**Cabeçalho:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b8ecc-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b8ecc-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ecc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ecc-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8ecc-114">See also</span></span>
- [<span data-ttu-id="b8ecc-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b8ecc-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
