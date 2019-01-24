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
ms.openlocfilehash: a94891b91f6ac14469e18ed6840a083ce5e9d64d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516909"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="86f6a-102">Método IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="86f6a-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="86f6a-103">Obtém a representação de cadeia de caracteres desse objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="86f6a-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="86f6a-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86f6a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="86f6a-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="86f6a-106">[out] Um ponteiro para uma cadeia de caracteres que é o objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="86f6a-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86f6a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="86f6a-107">Remarks</span></span>  
 <span data-ttu-id="86f6a-108">O `GetSerializedBuffer` método serializa o objeto para que ele pode ser empacotado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="86f6a-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f6a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="86f6a-109">Requirements</span></span>  
 <span data-ttu-id="86f6a-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86f6a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86f6a-111">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86f6a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86f6a-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="86f6a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86f6a-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86f6a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86f6a-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86f6a-114">See also</span></span>
- [<span data-ttu-id="86f6a-115">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="86f6a-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
