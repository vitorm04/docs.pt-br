---
title: Função GetErrorInfo (referência de API não gerenciada)
description: A função GetErrorInfo recupera informações de erro da chamada de função anterior.
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
ms.openlocfilehash: 9a80c0b5522113e704336cda29362a0406077931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553669"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="21328-103">Função GetErrorInfo</span><span class="sxs-lookup"><span data-stu-id="21328-103">GetErrorInfo function</span></span>
<span data-ttu-id="21328-104">Recupera informações de erro da chamada de função anterior.</span><span class="sxs-lookup"><span data-stu-id="21328-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="21328-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21328-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo();
```  

## <a name="return-value"></a><span data-ttu-id="21328-106">Retornar valor</span><span class="sxs-lookup"><span data-stu-id="21328-106">Return value</span></span>

<span data-ttu-id="21328-107">Um ponteiro para um objeto [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) se a chamada de função for bem-sucedida ou `null` se falhar.</span><span class="sxs-lookup"><span data-stu-id="21328-107">An pointer to an [IErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="21328-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="21328-108">Remarks</span></span>

<span data-ttu-id="21328-109">Essa função encapsula uma chamada para o método [IComThreadingInfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="21328-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="21328-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21328-110">Requirements</span></span>  
 <span data-ttu-id="21328-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21328-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21328-112">**Cabeçalho:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="21328-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="21328-113">**.NET Framework versões:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="21328-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21328-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="21328-114">See also</span></span>

- [<span data-ttu-id="21328-115">WMI e Contadores de Desempenho (Referência de API Não Gerenciada)</span><span class="sxs-lookup"><span data-stu-id="21328-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
