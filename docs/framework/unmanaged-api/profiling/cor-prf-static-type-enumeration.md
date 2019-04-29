---
title: Enumeração COR_PRF_STATIC_TYPE
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 310915ce84819a2a5a2d5e1f22356b61c16e7ec7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599007"
---
# <a name="corprfstatictype-enumeration"></a><span data-ttu-id="eb6ea-102">Enumeração COR_PRF_STATIC_TYPE</span><span class="sxs-lookup"><span data-stu-id="eb6ea-102">COR_PRF_STATIC_TYPE Enumeration</span></span>
<span data-ttu-id="eb6ea-103">Indica se um campo é estático e, em caso positivo, a qualidade estática aplicada ao campo.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-103">Indicates whether a field is static and, if so, the static quality that applies to the field.</span></span> <span data-ttu-id="eb6ea-104">Esses valores podem ser combinados usando a operação OR bit a bit para indicar que o campo tem várias qualidades estáticas diferentes.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-104">These values can be combined using the bitwise OR operation to indicate that the field has multiple, different static qualities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb6ea-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb6ea-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="eb6ea-106">Membros</span><span class="sxs-lookup"><span data-stu-id="eb6ea-106">Members</span></span>  
  
|<span data-ttu-id="eb6ea-107">Membro</span><span class="sxs-lookup"><span data-stu-id="eb6ea-107">Member</span></span>|<span data-ttu-id="eb6ea-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="eb6ea-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|<span data-ttu-id="eb6ea-109">O campo não é estático.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-109">The field is not static.</span></span>|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|<span data-ttu-id="eb6ea-110">O campo é estático de domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-110">The field is application domain-static.</span></span>|  
|`COR_PRF_FIELD_THREAD_STATIC`|<span data-ttu-id="eb6ea-111">O campo é de thread estático.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-111">The field is thread-static.</span></span>|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|<span data-ttu-id="eb6ea-112">O campo é o contexto estático.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-112">The field is context-static.</span></span>|  
|`COR_PRF_FIELD_RVA_STATIC`|<span data-ttu-id="eb6ea-113">O campo é o endereço virtual relativo (RVA)-estático.</span><span class="sxs-lookup"><span data-stu-id="eb6ea-113">The field is relative virtual address (RVA)-static.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb6ea-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb6ea-114">Requirements</span></span>  
 <span data-ttu-id="eb6ea-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb6ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb6ea-116">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb6ea-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb6ea-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb6ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb6ea-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb6ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb6ea-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb6ea-119">See also</span></span>

- [<span data-ttu-id="eb6ea-120">Criando perfil de enumerações</span><span class="sxs-lookup"><span data-stu-id="eb6ea-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
