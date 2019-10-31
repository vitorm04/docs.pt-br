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
ms.openlocfilehash: 4a55ae265230c4da3cc0a19b06a7597be8661beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103256"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="669d5-102">Método IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="669d5-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="669d5-103">Obtém a representação da cadeia de caracteres deste objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="669d5-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669d5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="669d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="669d5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="669d5-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="669d5-106">fora Um ponteiro para uma cadeia de caracteres que é o objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="669d5-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="669d5-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="669d5-107">Remarks</span></span>  
 <span data-ttu-id="669d5-108">O método `GetSerializedBuffer` serializa o objeto para que ele possa ser empacotado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="669d5-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669d5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="669d5-109">Requirements</span></span>  
 <span data-ttu-id="669d5-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="669d5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="669d5-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="669d5-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="669d5-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="669d5-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="669d5-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="669d5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="669d5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="669d5-114">See also</span></span>

- [<span data-ttu-id="669d5-115">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="669d5-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
