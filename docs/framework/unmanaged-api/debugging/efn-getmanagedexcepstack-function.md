---
title: Função _EFN_GetManagedExcepStack
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e201b9a350c030da59e2b6ed27f84f570c8e621
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126653"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="ece71-102">Função _EFN_GetManagedExcepStack</span><span class="sxs-lookup"><span data-stu-id="ece71-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="ece71-103">Dado um endereço do objeto de exceção gerenciada, retorna uma versão de cadeia de caracteres de rastreamento de pilha contida dentro do.</span><span class="sxs-lookup"><span data-stu-id="ece71-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece71-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ece71-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ece71-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ece71-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="ece71-106">[in] O cliente que está sendo depurado.</span><span class="sxs-lookup"><span data-stu-id="ece71-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="ece71-107">[in] Um ponteiro de objeto gerenciado, derivado de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ece71-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="ece71-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="ece71-108">szStackString</span></span>  
 <span data-ttu-id="ece71-109">[out] Cadeia de caracteres retornada.</span><span class="sxs-lookup"><span data-stu-id="ece71-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="ece71-110">[out] O número de caracteres disponíveis no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ece71-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ece71-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="ece71-111">Remarks</span></span>  
 <span data-ttu-id="ece71-112">Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retornará o HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0xa0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="ece71-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ece71-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ece71-113">Requirements</span></span>  
 <span data-ttu-id="ece71-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ece71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece71-115">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="ece71-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 **<span data-ttu-id="ece71-116">Versão do .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ece71-116">.NET Framework Version:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ece71-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ece71-117">See also</span></span>

- [<span data-ttu-id="ece71-118">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ece71-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
