---
title: "Enumeração CorDebugCodeInvokePurpose"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugInvokePurpose
api_location: mscordbi.dll
api_type: COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e87e5d8baf3ff7c87efe8f6bd96f8fd806527363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="cb487-102">Enumeração CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="cb487-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="cb487-103">Descreve por que uma função exportada chama o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cb487-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb487-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb487-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="cb487-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cb487-105">Members</span></span>  
  
|<span data-ttu-id="cb487-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cb487-106">Member</span></span>|<span data-ttu-id="cb487-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cb487-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="cb487-108">Nenhum ou desconhecido.</span><span class="sxs-lookup"><span data-stu-id="cb487-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="cb487-109">O código gerenciado será executado em qualquer ponto de entrada gerenciado, como um p-invoke inverso.</span><span class="sxs-lookup"><span data-stu-id="cb487-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="cb487-110">Qualquer finalidade mais detalhada é desconhecida pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cb487-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="cb487-111">O código gerenciado executará um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="cb487-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="cb487-112">O código gerenciado executará a implementação de um método de interface que foi chamado.</span><span class="sxs-lookup"><span data-stu-id="cb487-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb487-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb487-113">Remarks</span></span>  
 <span data-ttu-id="cb487-114">Essa enumeração é usada pelo [Icordebugprocess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) método para fornecer informações sobre percorrendo o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="cb487-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb487-115">Essa enumeração é destinada ao uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="cb487-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb487-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cb487-116">Requirements</span></span>  
 <span data-ttu-id="cb487-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb487-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb487-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb487-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb487-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb487-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb487-120">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb487-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb487-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb487-121">See Also</span></span>  
 [<span data-ttu-id="cb487-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="cb487-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="cb487-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="cb487-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
