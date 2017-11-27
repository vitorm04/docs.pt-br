---
title: Estrutura BucketParameters
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: BucketParameters
api_location: mscoree.dll
api_type: COM
f1_keywords: BucketParameters
helpviewer_keywords: BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7626ce6b2b6278be7cd9989718c13f7c98e4ace3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="865b7-102">Estrutura BucketParameters</span><span class="sxs-lookup"><span data-stu-id="865b7-102">BucketParameters Structure</span></span>
<span data-ttu-id="865b7-103">Armazena o nome de um evento e os parâmetros de tipo para a exceção atual que está associado com o evento.</span><span class="sxs-lookup"><span data-stu-id="865b7-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="865b7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="865b7-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="865b7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="865b7-105">Members</span></span>  
  
|<span data-ttu-id="865b7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="865b7-106">Member</span></span>|<span data-ttu-id="865b7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="865b7-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="865b7-108">`true`, se o restante dessa estrutura é válido. Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="865b7-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="865b7-109">Nome do tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="865b7-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="865b7-110">Uma matriz de cadeias de caracteres, cada uma delas Especifica um parâmetro para a exceção atual associado ao evento.</span><span class="sxs-lookup"><span data-stu-id="865b7-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="865b7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="865b7-111">Requirements</span></span>  
 <span data-ttu-id="865b7-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="865b7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="865b7-113">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="865b7-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="865b7-114">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="865b7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865b7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="865b7-115">See Also</span></span>  
 [<span data-ttu-id="865b7-116">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="865b7-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
