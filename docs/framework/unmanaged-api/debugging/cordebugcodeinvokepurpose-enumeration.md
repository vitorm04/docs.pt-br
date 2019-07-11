---
title: Enumeração CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 593644802fa490c80b361bfdad3473abe4e82922
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740283"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="a3d6a-102">Enumeração CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="a3d6a-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="a3d6a-103">Descreve por que uma função exportada chama o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3d6a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a3d6a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="a3d6a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a3d6a-105">Members</span></span>  
  
|<span data-ttu-id="a3d6a-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a3d6a-106">Member</span></span>|<span data-ttu-id="a3d6a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a3d6a-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="a3d6a-108">Nenhum ou desconhecido.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="a3d6a-109">O código gerenciado será executado em qualquer ponto de entrada gerenciado, como um p-invoke inverso.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="a3d6a-110">Qualquer finalidade mais detalhada é desconhecida pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="a3d6a-111">O código gerenciado executará um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="a3d6a-112">O código gerenciado executará a implementação de um método de interface que foi chamado.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3d6a-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a3d6a-113">Remarks</span></span>  
 <span data-ttu-id="a3d6a-114">Essa enumeração é usada pelo [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) método para fornecer informações sobre como percorrer o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3d6a-115">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="a3d6a-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3d6a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a3d6a-116">Requirements</span></span>  
 <span data-ttu-id="a3d6a-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3d6a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3d6a-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3d6a-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3d6a-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3d6a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3d6a-120">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3d6a-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3d6a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a3d6a-121">See also</span></span>

- [<span data-ttu-id="a3d6a-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a3d6a-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="a3d6a-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="a3d6a-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
