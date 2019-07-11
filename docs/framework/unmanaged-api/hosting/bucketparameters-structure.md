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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96fee259b31938ddec5820bc1b8d72a96b50c8d8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773886"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="3eab1-102">Estrutura BucketParameters</span><span class="sxs-lookup"><span data-stu-id="3eab1-102">BucketParameters Structure</span></span>
<span data-ttu-id="3eab1-103">Armazena o nome do tipo de um evento e os parâmetros para a exceção atual que está associado com o evento.</span><span class="sxs-lookup"><span data-stu-id="3eab1-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eab1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3eab1-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="3eab1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3eab1-105">Members</span></span>  
  
|<span data-ttu-id="3eab1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3eab1-106">Member</span></span>|<span data-ttu-id="3eab1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3eab1-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="3eab1-108">`true`, se o restante dessa estrutura é válido. Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3eab1-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="3eab1-109">Nome do tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="3eab1-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="3eab1-110">Uma matriz de cadeias de caracteres, cada um deles especifica um parâmetro para a exceção atual associado ao evento.</span><span class="sxs-lookup"><span data-stu-id="3eab1-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3eab1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3eab1-111">Requirements</span></span>  
 <span data-ttu-id="3eab1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3eab1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3eab1-113">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="3eab1-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3eab1-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3eab1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eab1-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3eab1-115">See also</span></span>

- [<span data-ttu-id="3eab1-116">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3eab1-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
