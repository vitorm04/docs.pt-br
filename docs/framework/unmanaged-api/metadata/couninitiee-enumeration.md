---
title: "Enumeração COUNINITIEE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COUNINITIEE
api_location: mscoree.dll
api_type: COM
f1_keywords: COUNINITIEE
helpviewer_keywords: COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 808320a2034011793429f1805edea82a52add23d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="dc374-102">Enumeração COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="dc374-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="dc374-103">Especifica constantes usadas pelo [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ao inicializar o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="dc374-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc374-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dc374-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="dc374-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dc374-105">Members</span></span>  
  
|<span data-ttu-id="dc374-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dc374-106">Member</span></span>|<span data-ttu-id="dc374-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc374-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="dc374-108">Indica o modo de cancelamento inicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="dc374-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="dc374-109">Indica o modo de cancelamento inicialização de descarregamento de um assembly.</span><span class="sxs-lookup"><span data-stu-id="dc374-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc374-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc374-110">Requirements</span></span>  
 <span data-ttu-id="dc374-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc374-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc374-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dc374-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dc374-113">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="dc374-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dc374-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc374-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc374-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc374-115">See Also</span></span>  
 [<span data-ttu-id="dc374-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="dc374-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
