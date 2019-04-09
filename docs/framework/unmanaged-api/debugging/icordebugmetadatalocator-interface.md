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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108818"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="93289-102">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="93289-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="93289-103">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="93289-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="93289-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="93289-104">Methods</span></span>  
  
|<span data-ttu-id="93289-105">Método</span><span class="sxs-lookup"><span data-stu-id="93289-105">Method</span></span>|<span data-ttu-id="93289-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="93289-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93289-107">Método GetMetaData</span><span class="sxs-lookup"><span data-stu-id="93289-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="93289-108">Solicita que o depurador para retornar o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitado do depurador.</span><span class="sxs-lookup"><span data-stu-id="93289-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93289-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="93289-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93289-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="93289-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93289-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93289-111">Requirements</span></span>  
 <span data-ttu-id="93289-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93289-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93289-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93289-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93289-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93289-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="93289-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="93289-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="93289-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93289-116">See also</span></span>

- [<span data-ttu-id="93289-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="93289-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="93289-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="93289-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
