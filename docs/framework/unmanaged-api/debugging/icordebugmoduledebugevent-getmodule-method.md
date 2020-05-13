---
title: 'Método ICorDebugModuleDebugEvent:: GetModule'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213355"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="16c3a-102">Método ICorDebugModuleDebugEvent:: GetModule</span><span class="sxs-lookup"><span data-stu-id="16c3a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>
<span data-ttu-id="16c3a-103">Obtém o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="16c3a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c3a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16c3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16c3a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="16c3a-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="16c3a-106">fora Um ponteiro para o endereço de um objeto ICorDebugModule que representa o módulo mesclado que acabou de ser carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="16c3a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16c3a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="16c3a-107">Remarks</span></span>  
 <span data-ttu-id="16c3a-108">Você pode chamar o método [GetEventKind](icordebugdebugevent-geteventkind-method.md) para determinar se o módulo foi carregado ou descarregado.</span><span class="sxs-lookup"><span data-stu-id="16c3a-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="16c3a-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="16c3a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c3a-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="16c3a-110">Requirements</span></span>  
 <span data-ttu-id="16c3a-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c3a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c3a-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16c3a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c3a-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c3a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c3a-114">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c3a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16c3a-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="16c3a-115">See also</span></span>

- [<span data-ttu-id="16c3a-116">Interface ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="16c3a-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="16c3a-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="16c3a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
