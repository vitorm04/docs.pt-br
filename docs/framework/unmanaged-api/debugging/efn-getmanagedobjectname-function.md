---
title: Função _EFN_GetManagedObjectName
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3490477f30cd1c0badaa9cfd71433a5bf9d7a99
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738987"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="37e77-102">\_EFN\_GetManagedObjectName função</span><span class="sxs-lookup"><span data-stu-id="37e77-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="37e77-103">Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.</span><span class="sxs-lookup"><span data-stu-id="37e77-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37e77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37e77-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37e77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37e77-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="37e77-106">[in] Um ponteiro para o cliente de depuração.</span><span class="sxs-lookup"><span data-stu-id="37e77-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="37e77-107">[in] Um ponteiro de objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="37e77-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="37e77-108">szName</span><span class="sxs-lookup"><span data-stu-id="37e77-108">szName</span></span>  
 <span data-ttu-id="37e77-109">[out] O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="37e77-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="37e77-110">[out] O número de caracteres disponíveis no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="37e77-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37e77-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="37e77-111">Remarks</span></span>  
 <span data-ttu-id="37e77-112">Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retornará o HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0xa0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="37e77-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37e77-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37e77-113">Requirements</span></span>  
 <span data-ttu-id="37e77-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37e77-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37e77-115">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="37e77-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="37e77-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37e77-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e77-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37e77-117">See also</span></span>

- [<span data-ttu-id="37e77-118">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="37e77-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
