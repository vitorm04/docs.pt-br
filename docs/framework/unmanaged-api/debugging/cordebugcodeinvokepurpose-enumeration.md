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
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179239"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="5e495-102">Enumeração CorDebugCodeInvokePurpose</span><span class="sxs-lookup"><span data-stu-id="5e495-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="5e495-103">Descreve por que uma função exportada chama código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5e495-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e495-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e495-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="5e495-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5e495-105">Members</span></span>  
  
|<span data-ttu-id="5e495-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5e495-106">Member</span></span>|<span data-ttu-id="5e495-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e495-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="5e495-108">Nenhum ou desconhecido.</span><span class="sxs-lookup"><span data-stu-id="5e495-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="5e495-109">O código gerenciado será executado em qualquer ponto de entrada gerenciado, como um p-invoke inverso.</span><span class="sxs-lookup"><span data-stu-id="5e495-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="5e495-110">Qualquer finalidade mais detalhada é desconhecida pelo runtime.</span><span class="sxs-lookup"><span data-stu-id="5e495-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="5e495-111">O código gerenciado executará um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="5e495-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="5e495-112">O código gerenciado executará a implementação de um método de interface que foi chamado.</span><span class="sxs-lookup"><span data-stu-id="5e495-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e495-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="5e495-113">Remarks</span></span>  
 <span data-ttu-id="5e495-114">Essa enumeração é usada pelo método [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) para fornecer informações sobre a revisão do código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5e495-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e495-115">Esta enumeração destina-se a ser usada apenas em cenários de depuração nativos .NET.</span><span class="sxs-lookup"><span data-stu-id="5e495-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e495-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e495-116">Requirements</span></span>  
 <span data-ttu-id="5e495-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e495-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e495-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e495-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e495-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e495-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e495-120">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e495-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e495-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e495-121">See also</span></span>

- [<span data-ttu-id="5e495-122">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="5e495-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="5e495-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="5e495-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
