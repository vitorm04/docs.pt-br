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
ms.openlocfilehash: c1ee52e993859963984f7468e41a5daf3a77ba26
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621663"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="b4506-102">Interface ICorDebugMetaDataLocator</span><span class="sxs-lookup"><span data-stu-id="b4506-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="b4506-103">Fornece informações de metadados ao depurador.</span><span class="sxs-lookup"><span data-stu-id="b4506-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4506-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="b4506-104">Methods</span></span>  
  
|<span data-ttu-id="b4506-105">Método</span><span class="sxs-lookup"><span data-stu-id="b4506-105">Method</span></span>|<span data-ttu-id="b4506-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4506-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4506-107">Método GetMetaData</span><span class="sxs-lookup"><span data-stu-id="b4506-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="b4506-108">Solicita que o depurador para retornar o caminho completo para um módulo cujos metadados são necessários para concluir uma operação solicitado do depurador.</span><span class="sxs-lookup"><span data-stu-id="b4506-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4506-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4506-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4506-110">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="b4506-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4506-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b4506-111">Requirements</span></span>  
 <span data-ttu-id="b4506-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4506-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4506-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4506-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4506-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4506-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4506-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4506-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4506-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4506-116">See also</span></span>
- [<span data-ttu-id="b4506-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b4506-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b4506-118">Depuração</span><span class="sxs-lookup"><span data-stu-id="b4506-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
