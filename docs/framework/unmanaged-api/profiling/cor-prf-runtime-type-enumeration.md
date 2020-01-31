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
ms.openlocfilehash: c1767e718e597918ef59b72a4b7acc3589421de0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867049"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="2560e-102">Enumeração COR_PRF_RUNTIME_TYPE</span><span class="sxs-lookup"><span data-stu-id="2560e-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="2560e-103">Contém valores que indicam a versão do Common Language Runtime (CLR): área de trabalho ou CoreCLR, que é usada no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2560e-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2560e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2560e-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="2560e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2560e-105">Members</span></span>  
  
|<span data-ttu-id="2560e-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="2560e-106">Member</span></span>|<span data-ttu-id="2560e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2560e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="2560e-108">A versão da área de trabalho do CLR.</span><span class="sxs-lookup"><span data-stu-id="2560e-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="2560e-109">A versão principal do CLR, usada no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2560e-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2560e-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2560e-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2560e-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="2560e-111">Requirements</span></span>  
 <span data-ttu-id="2560e-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2560e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2560e-113">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2560e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2560e-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2560e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2560e-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2560e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2560e-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="2560e-116">See also</span></span>

- [<span data-ttu-id="2560e-117">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="2560e-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
