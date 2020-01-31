---
title: Interface ICorDebugMetaDataLocator
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: dd31bf458dde043a04e24251cedcac585fd385f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793037"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="e4230-102">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="e4230-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="e4230-103">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="e4230-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4230-104">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="e4230-104">Methods</span></span>  
  
|<span data-ttu-id="e4230-105">Método</span><span class="sxs-lookup"><span data-stu-id="e4230-105">Method</span></span>|<span data-ttu-id="e4230-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4230-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4230-107">Método GetMetaData</span><span class="sxs-lookup"><span data-stu-id="e4230-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="e4230-108">Solicita que o depurador retorne o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitada pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="e4230-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4230-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4230-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e4230-110">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="e4230-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4230-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="e4230-111">Requirements</span></span>  
 <span data-ttu-id="e4230-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4230-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4230-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4230-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4230-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4230-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4230-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4230-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4230-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="e4230-116">See also</span></span>

- [<span data-ttu-id="e4230-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e4230-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e4230-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="e4230-118">Debugging</span></span>](index.md)
