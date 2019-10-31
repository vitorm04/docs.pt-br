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
ms.openlocfilehash: 062dc62dfe53af3bf5158cb1add0897eccc1df60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102608"
---
# <a name="geterrorinfo-function"></a><span data-ttu-id="b6bf9-103">Função GetErrorInfo</span><span class="sxs-lookup"><span data-stu-id="b6bf9-103">GetErrorInfo function</span></span>
<span data-ttu-id="b6bf9-104">Recupera informações de erro da chamada de função anterior.</span><span class="sxs-lookup"><span data-stu-id="b6bf9-104">Retrieves error information from the previous function call.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b6bf9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6bf9-105">Syntax</span></span>  
  
```cpp  
IErrorInfo* GetErrorInfo(); 
```  

## <a name="return-value"></a><span data-ttu-id="b6bf9-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b6bf9-106">Return value</span></span>

<span data-ttu-id="b6bf9-107">Um ponteiro para um objeto [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) se a chamada de função for bem-sucedida ou `null` se falhar.</span><span class="sxs-lookup"><span data-stu-id="b6bf9-107">An pointer to an [IErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo) object if the function call succeeds, or `null` if it fails.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b6bf9-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6bf9-108">Remarks</span></span>

<span data-ttu-id="b6bf9-109">Essa função encapsula uma chamada para o método [IComThreadingInfo:: GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) .</span><span class="sxs-lookup"><span data-stu-id="b6bf9-109">This function wraps a call to the [IComThreadingInfo::GetErrorInfo](/windows/desktop/api/objidlbase/nf-objidlbase-icomthreadinginfo-getcurrentapartmenttype) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6bf9-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6bf9-110">Requirements</span></span>  
 <span data-ttu-id="b6bf9-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6bf9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6bf9-112">**Cabeçalho:** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="b6bf9-112">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b6bf9-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b6bf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6bf9-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6bf9-114">See also</span></span>

- [<span data-ttu-id="b6bf9-115">WMI e contadores de desempenho (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="b6bf9-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
