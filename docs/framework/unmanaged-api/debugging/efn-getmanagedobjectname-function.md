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
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123003"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="8c344-102">Função \_EFN\_GetManagedObjectName</span><span class="sxs-lookup"><span data-stu-id="8c344-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="8c344-103">Obtém o nome de um tipo usando o ponteiro de objeto gerenciado fornecido.</span><span class="sxs-lookup"><span data-stu-id="8c344-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c344-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c344-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c344-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c344-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="8c344-106">no Um ponteiro para o cliente de depuração.</span><span class="sxs-lookup"><span data-stu-id="8c344-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="8c344-107">no Um ponteiro de objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8c344-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="8c344-108">szName</span><span class="sxs-lookup"><span data-stu-id="8c344-108">szName</span></span>  
 <span data-ttu-id="8c344-109">fora O nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="8c344-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="8c344-110">fora O número de caracteres disponíveis no buffer de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8c344-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c344-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c344-111">Remarks</span></span>  
 <span data-ttu-id="8c344-112">Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0XA0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="8c344-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c344-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8c344-113">Requirements</span></span>  
 <span data-ttu-id="8c344-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c344-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c344-115">**Cabeçalho:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="8c344-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="8c344-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c344-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c344-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c344-117">See also</span></span>

- [<span data-ttu-id="8c344-118">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="8c344-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
