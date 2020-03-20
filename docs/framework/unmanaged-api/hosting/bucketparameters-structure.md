---
title: Estrutura BucketParameters
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178283"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="30e3d-102">Estrutura BucketParameters</span><span class="sxs-lookup"><span data-stu-id="30e3d-102">BucketParameters Structure</span></span>
<span data-ttu-id="30e3d-103">Armazena o nome do tipo de um evento e os parâmetros para a exceção atual que está associada ao evento.</span><span class="sxs-lookup"><span data-stu-id="30e3d-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e3d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30e3d-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="30e3d-105">Membros</span><span class="sxs-lookup"><span data-stu-id="30e3d-105">Members</span></span>  
  
|<span data-ttu-id="30e3d-106">Membro</span><span class="sxs-lookup"><span data-stu-id="30e3d-106">Member</span></span>|<span data-ttu-id="30e3d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="30e3d-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="30e3d-108">`true`, se o resto desta estrutura for válida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="30e3d-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="30e3d-109">Nome do tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="30e3d-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="30e3d-110">Uma matriz de strings, cada uma das quais especifica um parâmetro para a exceção atual associada ao evento.</span><span class="sxs-lookup"><span data-stu-id="30e3d-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30e3d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="30e3d-111">Requirements</span></span>  
 <span data-ttu-id="30e3d-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30e3d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e3d-113">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="30e3d-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="30e3d-114">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30e3d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e3d-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="30e3d-115">See also</span></span>

- [<span data-ttu-id="30e3d-116">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="30e3d-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
