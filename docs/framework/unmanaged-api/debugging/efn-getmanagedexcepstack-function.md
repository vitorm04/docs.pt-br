---
title: "Função _EFN_GetManagedExcepStack"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edcd93bec29c6f0fef3b0bed4b8293efead3932d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="cf9e4-102">Função _EFN_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="cf9e4-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="cf9e4-103">Fornecido um endereço de objeto de exceção gerenciado, retorna uma versão de cadeia de caracteres de rastreamento de pilha contido.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf9e4-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf9e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf9e4-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="cf9e4-106">[in] O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="cf9e4-107">[in] Um ponteiro de objeto gerenciado, derivado de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="cf9e4-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="cf9e4-108">szStackString</span></span>  
 <span data-ttu-id="cf9e4-109">[out] A cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="cf9e4-110">[out] O número de caracteres disponíveis no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf9e4-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf9e4-111">Remarks</span></span>  
 <span data-ttu-id="cf9e4-112">Não se houver nenhum código gerenciado no thread no momento no contexto, a função retorna o HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0xa0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="cf9e4-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf9e4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf9e4-113">Requirements</span></span>  
 <span data-ttu-id="cf9e4-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9e4-115">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="cf9e4-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="cf9e4-116">**Versão do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9e4-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9e4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf9e4-117">See Also</span></span>  
 [<span data-ttu-id="cf9e4-118">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="cf9e4-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
