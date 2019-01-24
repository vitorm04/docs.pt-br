---
title: Estrutura StackOverflowInfo
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c1723facca3c547c275ee44f0abefe21a177eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572023"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="3bce5-102">Estrutura StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="3bce5-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="3bce5-103">Armazena o tipo de estouro que ocorreram e informações sobre a exceção que foi gerada devido ao estouro.</span><span class="sxs-lookup"><span data-stu-id="3bce5-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bce5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3bce5-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="3bce5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3bce5-105">Members</span></span>  
  
|<span data-ttu-id="3bce5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3bce5-106">Member</span></span>|<span data-ttu-id="3bce5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3bce5-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="3bce5-108">Um valor igual a [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeração que especifica o tipo de estouro.</span><span class="sxs-lookup"><span data-stu-id="3bce5-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="3bce5-109">Um ponteiro para um Win32 `EXCEPTION_POINTERS` objeto, que contém um registro de exceção com uma descrição independente de máquina de uma exceção e um registro de contexto com uma descrição de máquina dependente de contexto do processador no momento da exceção.</span><span class="sxs-lookup"><span data-stu-id="3bce5-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3bce5-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="3bce5-110">Remarks</span></span>  
 <span data-ttu-id="3bce5-111">Um `StackOverflowInfo` objeto é passado para o [iactiononclrevent:: ONEVENT](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método para `Event_StackOverflow` eventos.</span><span class="sxs-lookup"><span data-stu-id="3bce5-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bce5-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3bce5-112">Requirements</span></span>  
 <span data-ttu-id="3bce5-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bce5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bce5-114">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="3bce5-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="3bce5-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3bce5-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3bce5-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bce5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bce5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bce5-117">See also</span></span>
- [<span data-ttu-id="3bce5-118">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="3bce5-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
