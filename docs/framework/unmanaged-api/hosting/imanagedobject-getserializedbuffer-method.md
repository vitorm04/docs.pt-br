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
ms.openlocfilehash: c68ec0b41bb38afc7cefaf47df718fffcf42d250
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842421"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="8db75-102">Método IManagedObject::GetSerializedBuffer</span><span class="sxs-lookup"><span data-stu-id="8db75-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="8db75-103">Obtém a representação da cadeia de caracteres deste objeto gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8db75-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8db75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8db75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8db75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8db75-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="8db75-106">fora Um ponteiro para uma cadeia de caracteres que é o objeto serializado.</span><span class="sxs-lookup"><span data-stu-id="8db75-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8db75-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8db75-107">Remarks</span></span>  
 <span data-ttu-id="8db75-108">O `GetSerializedBuffer` método serializa o objeto para que ele possa ser empacotado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="8db75-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db75-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8db75-109">Requirements</span></span>  
 <span data-ttu-id="8db75-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8db75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8db75-111">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8db75-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8db75-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8db75-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8db75-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8db75-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db75-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8db75-114">See also</span></span>

- [<span data-ttu-id="8db75-115">Interface IManagedObject</span><span class="sxs-lookup"><span data-stu-id="8db75-115">IManagedObject Interface</span></span>](imanagedobject-interface.md)
