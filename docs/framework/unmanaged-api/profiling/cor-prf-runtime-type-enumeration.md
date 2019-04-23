---
title: Enumeração COR_PRF_RUNTIME_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e57c622780f0bc92061fd2928ea861f904d9eb37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122103"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="f15b5-102">Enumeração COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="f15b5-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="f15b5-103">Contém valores que indicam a versão do common language runtime (CLR): área de trabalho ou no CoreCLR, que é usado no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="f15b5-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f15b5-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="f15b5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f15b5-105">Members</span></span>  
  
|<span data-ttu-id="f15b5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f15b5-106">Member</span></span>|<span data-ttu-id="f15b5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f15b5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="f15b5-108">A versão da área de trabalho do CLR.</span><span class="sxs-lookup"><span data-stu-id="f15b5-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="f15b5-109">A versão principal do CLR, usado no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="f15b5-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f15b5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f15b5-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15b5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f15b5-111">Requirements</span></span>  
 <span data-ttu-id="f15b5-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f15b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15b5-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f15b5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f15b5-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f15b5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f15b5-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15b5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f15b5-116">See also</span></span>

- [<span data-ttu-id="f15b5-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="f15b5-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
