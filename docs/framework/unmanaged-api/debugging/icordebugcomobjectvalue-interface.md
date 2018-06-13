---
title: Interface ICorDebugComObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412507"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="519cb-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="519cb-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="519cb-103">Fornece métodos para recuperar as informações associadas a um runtime callable wrapper (RCW).</span><span class="sxs-lookup"><span data-stu-id="519cb-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="519cb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="519cb-104">Methods</span></span>  
  
|<span data-ttu-id="519cb-105">Método</span><span class="sxs-lookup"><span data-stu-id="519cb-105">Method</span></span>|<span data-ttu-id="519cb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="519cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="519cb-107">Método GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="519cb-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="519cb-108">Obtém os ponteiros de interface bruto em cache no RCW atual.</span><span class="sxs-lookup"><span data-stu-id="519cb-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="519cb-109">Método GetCachedInterfaceTypes</span><span class="sxs-lookup"><span data-stu-id="519cb-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="519cb-110">Fornece um enumerador para os tipos de interface que o objeto atual foi maiusculas e minúsculas para ou usado como.</span><span class="sxs-lookup"><span data-stu-id="519cb-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="519cb-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="519cb-111">Remarks</span></span>  
 <span data-ttu-id="519cb-112">Para verificar se uma instância de uma interface de "ICorDebugValue" representa um RCW, chama um depurador `QueryInterface` em "ICorDebugValue" com `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="519cb-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="519cb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="519cb-113">Requirements</span></span>  
 <span data-ttu-id="519cb-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="519cb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="519cb-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="519cb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="519cb-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="519cb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="519cb-117">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="519cb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519cb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="519cb-118">See Also</span></span>  
 [<span data-ttu-id="519cb-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="519cb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="519cb-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="519cb-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
