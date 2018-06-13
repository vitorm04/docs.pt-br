---
title: Interface1 ICorDebugModule2
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 537023cf117477b54117799fc9ea62e894bb6591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419134"
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="9a88c-102">Interface1 ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="9a88c-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="9a88c-103">Serve como uma extensão lógica para a interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="9a88c-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a88c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9a88c-104">Methods</span></span>  
  
|<span data-ttu-id="9a88c-105">Método</span><span class="sxs-lookup"><span data-stu-id="9a88c-105">Method</span></span>|<span data-ttu-id="9a88c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a88c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a88c-107">Método ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="9a88c-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="9a88c-108">Aplica as alterações nos metadados e as alterações no código Microsoft intermediate language (MSIL) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="9a88c-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="9a88c-109">Método GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="9a88c-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="9a88c-110">Obtém os sinalizadores que controlam a compilação just-in-time (JIT) para este `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="9a88c-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="9a88c-111">Método ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="9a88c-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="9a88c-112">Resolve o assembly referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="9a88c-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="9a88c-113">Método SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="9a88c-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="9a88c-114">Define os sinalizadores que controlam a compilação JIT para este `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="9a88c-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="9a88c-115">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="9a88c-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="9a88c-116">Define o status de apenas meu código (JMC) de todos os métodos de todas as classes neste `ICorDebugModule2` para o valor especificado, exceto aqueles na `pTokens` matriz, que define como o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="9a88c-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a88c-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a88c-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a88c-118">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="9a88c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a88c-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a88c-119">Requirements</span></span>  
 <span data-ttu-id="9a88c-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a88c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a88c-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a88c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a88c-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a88c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a88c-123">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a88c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a88c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a88c-124">See Also</span></span>  
 [<span data-ttu-id="9a88c-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9a88c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
