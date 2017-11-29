---
title: "Enumeração CorSaveSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSaveSize
helpviewer_keywords: CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34d4d42c7cf385bca77de37dce52689778aa5b1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="2e162-102">Enumeração CorSaveSize</span><span class="sxs-lookup"><span data-stu-id="2e162-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="2e162-103">Contém valores que indica o nível de precisão necessária ao consultar o tamanho de um salvamento operação.</span><span class="sxs-lookup"><span data-stu-id="2e162-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e162-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e162-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="2e162-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2e162-105">Members</span></span>  
  
|<span data-ttu-id="2e162-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2e162-106">Member</span></span>|<span data-ttu-id="2e162-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2e162-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="2e162-108">Especifica que o valor de retorno deve ser exato.</span><span class="sxs-lookup"><span data-stu-id="2e162-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="2e162-109">Especifica que o valor de retorno deve ser estimado.</span><span class="sxs-lookup"><span data-stu-id="2e162-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="2e162-110">Especifica que tipos descartáveis devem ser removidos.</span><span class="sxs-lookup"><span data-stu-id="2e162-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e162-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e162-111">Requirements</span></span>  
 <span data-ttu-id="2e162-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e162-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e162-113">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="2e162-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2e162-114">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2e162-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e162-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e162-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e162-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e162-116">See Also</span></span>  
 [<span data-ttu-id="2e162-117">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="2e162-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
