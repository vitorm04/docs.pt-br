---
title: ICorDebugAppDomainEnum Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomainEnum
helpviewer_keywords:
- ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf8db3b02ba4766d046fc549eec8add31f51069
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407914"
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="2c460-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="2c460-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="2c460-103">Fornece o `Next` método, que retorna um número especificado de `ICorDebugAppDomainEnum` valores que começam no seguinte local na enumeração.</span><span class="sxs-lookup"><span data-stu-id="2c460-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="2c460-104">Esta interface é uma subclasse de "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="2c460-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c460-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2c460-105">Methods</span></span>  
  
|<span data-ttu-id="2c460-106">Método</span><span class="sxs-lookup"><span data-stu-id="2c460-106">Method</span></span>|<span data-ttu-id="2c460-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2c460-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c460-108">Método Next</span><span class="sxs-lookup"><span data-stu-id="2c460-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="2c460-109">Obtém o número de domínios de aplicativo especificado da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="2c460-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c460-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c460-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c460-111">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="2c460-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c460-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c460-112">Requirements</span></span>  
 <span data-ttu-id="2c460-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c460-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c460-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c460-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c460-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c460-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c460-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c460-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c460-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c460-117">See Also</span></span>  
 [<span data-ttu-id="2c460-118">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="2c460-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="2c460-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c460-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
