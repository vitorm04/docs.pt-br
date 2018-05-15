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
ms.openlocfilehash: b1e652588d27521a04015228e86eb9af9c53346e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="18bdb-102">Estrutura StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="18bdb-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="18bdb-103">Armazena o tipo de estouro ocorreu e informações sobre a exceção que foi gerada devido ao estouro.</span><span class="sxs-lookup"><span data-stu-id="18bdb-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18bdb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18bdb-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="18bdb-105">Membros</span><span class="sxs-lookup"><span data-stu-id="18bdb-105">Members</span></span>  
  
|<span data-ttu-id="18bdb-106">Membro</span><span class="sxs-lookup"><span data-stu-id="18bdb-106">Member</span></span>|<span data-ttu-id="18bdb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="18bdb-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="18bdb-108">Um valor de [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeração que especifica o tipo de estouro.</span><span class="sxs-lookup"><span data-stu-id="18bdb-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="18bdb-109">Um ponteiro para um Win32 `EXCEPTION_POINTERS` objeto, que contém um registro de exceção com uma descrição independente de máquina de uma exceção e um registro de contexto com uma descrição de máquina dependente de contexto do processador no momento da exceção.</span><span class="sxs-lookup"><span data-stu-id="18bdb-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18bdb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="18bdb-110">Remarks</span></span>  
 <span data-ttu-id="18bdb-111">Um `StackOverflowInfo` objeto é passado para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método `Event_StackOverflow` eventos.</span><span class="sxs-lookup"><span data-stu-id="18bdb-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18bdb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18bdb-112">Requirements</span></span>  
 <span data-ttu-id="18bdb-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18bdb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18bdb-114">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="18bdb-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="18bdb-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="18bdb-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18bdb-116">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18bdb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18bdb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18bdb-117">See Also</span></span>  
 [<span data-ttu-id="18bdb-118">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="18bdb-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
