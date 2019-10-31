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
ms.openlocfilehash: b68f24908a5b214d507da8e8a4636a7c55259604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123013"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="708a8-102">Função \_EFN\_GetManagedObjectFieldInfo</span><span class="sxs-lookup"><span data-stu-id="708a8-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="708a8-103">Obtém o deslocamento do início de um objeto para um campo e o valor do campo, usando o ponteiro do objeto fornecido e o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="708a8-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="708a8-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="708a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="708a8-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="708a8-106">no Um ponteiro para o cliente de depuração.</span><span class="sxs-lookup"><span data-stu-id="708a8-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="708a8-107">no Um ponteiro de objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="708a8-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="708a8-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="708a8-108">szFieldName</span></span>  
 <span data-ttu-id="708a8-109">no Um ponteiro de objeto gerenciado para o nome do campo.</span><span class="sxs-lookup"><span data-stu-id="708a8-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="708a8-110">fora O valor do campo.</span><span class="sxs-lookup"><span data-stu-id="708a8-110">[out] The field value.</span></span> <span data-ttu-id="708a8-111">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="708a8-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="708a8-112">fora O deslocamento de `objAddr` para o campo.</span><span class="sxs-lookup"><span data-stu-id="708a8-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="708a8-113">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="708a8-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="708a8-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="708a8-114">Remarks</span></span>  
 <span data-ttu-id="708a8-115">Se o deslocamento for 0, nenhum deslocamento será gravado.</span><span class="sxs-lookup"><span data-stu-id="708a8-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="708a8-116">Se não houver nenhum código gerenciado no thread atualmente no contexto, a função retornará HRESULT SOS_E_NOMANAGEDCODE com um valor de recurso de 0XA0 e um código de erro de 0x1000.</span><span class="sxs-lookup"><span data-stu-id="708a8-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708a8-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="708a8-117">Requirements</span></span>  
 <span data-ttu-id="708a8-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="708a8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708a8-119">**Cabeçalho:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="708a8-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="708a8-120">**Versão do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708a8-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708a8-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="708a8-121">See also</span></span>

- [<span data-ttu-id="708a8-122">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="708a8-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
