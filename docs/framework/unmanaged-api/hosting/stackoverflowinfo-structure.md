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
ms.openlocfilehash: 1072026f92edbc646653c6dd74ec8e22d5b887e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105914"
---
# <a name="stackoverflowinfo-structure"></a><span data-ttu-id="035f9-102">Estrutura StackOverflowInfo</span><span class="sxs-lookup"><span data-stu-id="035f9-102">StackOverflowInfo Structure</span></span>
<span data-ttu-id="035f9-103">Armazena o tipo de estouro que ocorreu e informações sobre a exceção que foi lançada devido ao estouro.</span><span class="sxs-lookup"><span data-stu-id="035f9-103">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="035f9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="035f9-104">Syntax</span></span>  
  
```cpp  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="035f9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="035f9-105">Members</span></span>  
  
|<span data-ttu-id="035f9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="035f9-106">Member</span></span>|<span data-ttu-id="035f9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="035f9-107">Description</span></span>|  
|------------|-----------------|  
|`soType`|<span data-ttu-id="035f9-108">Um valor da enumeração [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) que especifica o tipo de estouro.</span><span class="sxs-lookup"><span data-stu-id="035f9-108">A value of the [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeration that specifies the type of overflow.</span></span>|  
|`pExceptionInfo`|<span data-ttu-id="035f9-109">Um ponteiro para um objeto de `EXCEPTION_POINTERS` do Win32, que contém um registro de exceção com uma descrição independente de computador de uma exceção e um registro de contexto com uma descrição dependente de computador do contexto do processador no momento da exceção.</span><span class="sxs-lookup"><span data-stu-id="035f9-109">A pointer to a Win32 `EXCEPTION_POINTERS` object, which contains an exception record with a machine-independent description of an exception and a context record with a machine-dependent description of the processor context at the time of the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="035f9-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="035f9-110">Remarks</span></span>  
 <span data-ttu-id="035f9-111">Um objeto `StackOverflowInfo` é passado para o método [IActionOnCLREvent:: OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) para eventos de `Event_StackOverflow`.</span><span class="sxs-lookup"><span data-stu-id="035f9-111">A `StackOverflowInfo` object is passed to the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method for `Event_StackOverflow` events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="035f9-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="035f9-112">Requirements</span></span>  
 <span data-ttu-id="035f9-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="035f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="035f9-114">**Cabeçalho:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="035f9-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="035f9-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="035f9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="035f9-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="035f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035f9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="035f9-117">See also</span></span>

- [<span data-ttu-id="035f9-118">Estruturas de hospedagem</span><span class="sxs-lookup"><span data-stu-id="035f9-118">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
