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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e9b9221aa2f5e048a94c225660ba2ac9214549c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108818"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="3a5ea-102">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="3a5ea-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="3a5ea-103">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="3a5ea-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a5ea-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="3a5ea-104">Methods</span></span>  
  
|<span data-ttu-id="3a5ea-105">Método</span><span class="sxs-lookup"><span data-stu-id="3a5ea-105">Method</span></span>|<span data-ttu-id="3a5ea-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a5ea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a5ea-107">Método GetMetaData</span><span class="sxs-lookup"><span data-stu-id="3a5ea-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="3a5ea-108">Solicita que o depurador para retornar o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitado do depurador.</span><span class="sxs-lookup"><span data-stu-id="3a5ea-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a5ea-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a5ea-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a5ea-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="3a5ea-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a5ea-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a5ea-111">Requirements</span></span>  
 <span data-ttu-id="3a5ea-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a5ea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a5ea-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a5ea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a5ea-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a5ea-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a5ea-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a5ea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a5ea-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a5ea-116">See also</span></span>

- [<span data-ttu-id="3a5ea-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="3a5ea-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3a5ea-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="3a5ea-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
