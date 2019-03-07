---
title: Função _EFN_GetManagedObjectFieldInfo
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 675bf2ad36fe5006a44890f8ccd6e6197f264ac1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484466"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="3e401-102">Função _EFN_GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="3e401-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="3e401-103">Obtém o deslocamento do início de um objeto para um campo e o valor do campo, usando o ponteiro de objeto fornecido e o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="3e401-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e401-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e401-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e401-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3e401-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="3e401-106">[in] Um ponteiro para o cliente de depuração.</span><span class="sxs-lookup"><span data-stu-id="3e401-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="3e401-107">[in] Um ponteiro de objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3e401-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="3e401-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="3e401-108">szFieldName</span></span>  
 <span data-ttu-id="3e401-109">[in] Um ponteiro de objeto gerenciado para o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="3e401-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3e401-110">[out] O valor do campo.</span><span class="sxs-lookup"><span data-stu-id="3e401-110">[out] The field value.</span></span> <span data-ttu-id="3e401-111">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="3e401-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="3e401-112">[out] O deslocamento do `objAddr` ao campo.</span><span class="sxs-lookup"><span data-stu-id="3e401-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="3e401-113">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="3e401-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e401-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e401-114">Remarks</span></span>  
 <span data-ttu-id="3e401-115">Se o deslocamento for 0, nenhum deslocamento é gravado.</span><span class="sxs-lookup"><span data-stu-id="3e401-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="3e401-116">Não se houver nenhum código gerenciado no thread atualmente no contexto, a função retornará o HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0xa0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="3e401-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e401-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e401-117">Requirements</span></span>  
 <span data-ttu-id="3e401-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e401-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e401-119">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="3e401-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="3e401-120">**Versão do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e401-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e401-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e401-121">See also</span></span>
- [<span data-ttu-id="3e401-122">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="3e401-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
