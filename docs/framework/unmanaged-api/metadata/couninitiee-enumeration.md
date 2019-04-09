---
title: Enumeração COUNINITIEE
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0cf1bfa03fd14d6324af60781003a8072a267a7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102941"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="e456b-102">Enumeração COUNINITIEE</span><span class="sxs-lookup"><span data-stu-id="e456b-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="e456b-103">Especifica as constantes usadas pelo [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) ao inicializar o common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e456b-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e456b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e456b-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="e456b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e456b-105">Members</span></span>  
  
|<span data-ttu-id="e456b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e456b-106">Member</span></span>|<span data-ttu-id="e456b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e456b-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="e456b-108">Indica o modo de desinicialização padrão.</span><span class="sxs-lookup"><span data-stu-id="e456b-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="e456b-109">Indica o modo de desinicialização para descarregar um assembly.</span><span class="sxs-lookup"><span data-stu-id="e456b-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e456b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e456b-110">Requirements</span></span>  
 <span data-ttu-id="e456b-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e456b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e456b-112">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e456b-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e456b-113">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e456b-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="e456b-114">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e456b-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e456b-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e456b-115">See also</span></span>

- [<span data-ttu-id="e456b-116">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="e456b-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
