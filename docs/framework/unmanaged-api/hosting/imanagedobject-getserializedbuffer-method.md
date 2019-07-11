---
title: Método IManagedObject::GetSerializedBuffer
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 65ac35e254368b53ac2751e84be7dfe052fa0b53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749077"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="5f345-102">Método IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="5f345-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="5f345-103">Obtém a representação de cadeia de caracteres desse objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5f345-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f345-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f345-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f345-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f345-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="5f345-106">[out] Um ponteiro para uma cadeia de caracteres que é o objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="5f345-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f345-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f345-107">Remarks</span></span>  
 <span data-ttu-id="5f345-108">O `GetSerializedBuffer` método serializa o objeto para que ele pode ser empacotado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5f345-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f345-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f345-109">Requirements</span></span>  
 <span data-ttu-id="5f345-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f345-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f345-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5f345-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5f345-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5f345-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5f345-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f345-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f345-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f345-114">See also</span></span>

- [<span data-ttu-id="5f345-115">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="5f345-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
