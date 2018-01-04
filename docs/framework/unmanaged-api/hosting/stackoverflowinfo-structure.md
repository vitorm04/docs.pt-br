---
title: Estrutura StackOverflowInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackOverflowInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: StackOverflowInfo
helpviewer_keywords: StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12a880a7c30277d382bff2b46ebe10720880e907
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="0bcb3-102">Estrutura StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="0bcb3-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="0bcb3-103">Armazena o tipo de estouro ocorreu e informações sobre a exceção que foi gerada devido ao estouro.</span><span class="sxs-lookup"><span data-stu-id="0bcb3-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bcb3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bcb3-104">Syntax</span></span>  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="0bcb3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="0bcb3-105">Members</span></span>  
  
|<span data-ttu-id="0bcb3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="0bcb3-106">Member</span></span>|<span data-ttu-id="0bcb3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bcb3-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="0bcb3-108">Um valor de [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeração que especifica o tipo de estouro.</span><span class="sxs-lookup"><span data-stu-id="0bcb3-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="0bcb3-109">Um ponteiro para um Win32 `EXCEPTION_POINTERS` objeto, que contém um registro de exceção com uma descrição independente de máquina de uma exceção e um registro de contexto com uma descrição de máquina dependente de contexto do processador no momento da exceção.</span><span class="sxs-lookup"><span data-stu-id="0bcb3-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bcb3-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bcb3-110">Remarks</span></span>  
 <span data-ttu-id="0bcb3-111">Um `StackOverflowInfo` objeto é passado para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método `Event_StackOverflow` eventos.</span><span class="sxs-lookup"><span data-stu-id="0bcb3-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bcb3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0bcb3-112">Requirements</span></span>  
 <span data-ttu-id="0bcb3-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bcb3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bcb3-114">**Cabeçalho:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0bcb3-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0bcb3-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0bcb3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0bcb3-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bcb3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bcb3-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bcb3-117">See Also</span></span>  
 [<span data-ttu-id="0bcb3-118">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="0bcb3-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
