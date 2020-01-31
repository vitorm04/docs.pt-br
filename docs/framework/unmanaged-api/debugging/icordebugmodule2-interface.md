---
title: Interface ICorDebugModule2
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
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792984"
---
# <a name="icordebugmodule2-interface"></a><span data-ttu-id="e29ec-102">Interface ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="e29ec-102">ICorDebugModule2 Interface</span></span>

<span data-ttu-id="e29ec-103">Serve como uma extensão lógica para a interface ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="e29ec-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e29ec-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e29ec-104">Methods</span></span>  
  
|<span data-ttu-id="e29ec-105">Método</span><span class="sxs-lookup"><span data-stu-id="e29ec-105">Method</span></span>|<span data-ttu-id="e29ec-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e29ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e29ec-107">Método ApplyChanges</span><span class="sxs-lookup"><span data-stu-id="e29ec-107">ApplyChanges Method</span></span>](icordebugmodule2-applychanges-method.md)|<span data-ttu-id="e29ec-108">Aplica as alterações nos metadados e as alterações no código MSIL (Microsoft Intermediate Language) para o processo em execução.</span><span class="sxs-lookup"><span data-stu-id="e29ec-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="e29ec-109">Método GetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="e29ec-109">GetJITCompilerFlags Method</span></span>](icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="e29ec-110">Obtém os sinalizadores que controlam a compilação JIT (just-in-time) para este `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="e29ec-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="e29ec-111">Método ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="e29ec-111">ResolveAssembly Method</span></span>](icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="e29ec-112">Resolve o assembly referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="e29ec-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="e29ec-113">Método SetJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="e29ec-113">SetJITCompilerFlags Method</span></span>](icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="e29ec-114">Define os sinalizadores que controlam a compilação JIT para este `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="e29ec-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="e29ec-115">Método SetJMCStatus</span><span class="sxs-lookup"><span data-stu-id="e29ec-115">SetJMCStatus Method</span></span>](icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="e29ec-116">Define o status de Apenas Meu Código (JMC) de todos os métodos de todas as classes neste `ICorDebugModule2` para o valor especificado, exceto aqueles na matriz de `pTokens`, que ele define para o valor oposto.</span><span class="sxs-lookup"><span data-stu-id="e29ec-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e29ec-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="e29ec-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e29ec-118">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="e29ec-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e29ec-119">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e29ec-119">Requirements</span></span>  
 <span data-ttu-id="e29ec-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e29ec-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e29ec-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e29ec-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e29ec-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e29ec-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e29ec-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e29ec-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e29ec-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="e29ec-124">See also</span></span>

- [<span data-ttu-id="e29ec-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e29ec-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
