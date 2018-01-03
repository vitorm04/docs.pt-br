---
title: "Função CLRDataCreateInstance"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataCreateInstance
api_location:
- mscordbi.dll
- mscordacwks.dll
api_type: COM
f1_keywords: CLRDataCreateInstance
helpviewer_keywords: CLRDataCreateInstance function [.NET Framework debugging]
ms.assetid: 440bad90-5a88-45e7-9157-4596801d8d19
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0740e80732e03ac6c1e7cf974d258113a181ea9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdatacreateinstance-function"></a><span data-ttu-id="ca9b4-102">Função CLRDataCreateInstance</span><span class="sxs-lookup"><span data-stu-id="ca9b4-102">CLRDataCreateInstance Function</span></span>
<span data-ttu-id="ca9b4-103">Cria um objeto de interface para o item de destino especificado.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-103">Creates an interface object for the specified target item.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca9b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca9b4-104">Syntax</span></span>  
  
```  
HRESULT CLRDataCreateInstance (  
    [in]  REFIID           iid,   
    [in]  ICLRDataTarget  *target,   
    [out] void           **iface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ca9b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca9b4-105">Parameters</span></span>  
 `iid`  
 <span data-ttu-id="ca9b4-106">[in] O identificador da interface a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-106">[in] The identifier of the interface to be instantiated.</span></span>  
  
 `target`  
 <span data-ttu-id="ca9b4-107">[in] Um ponteiro para um usuário implementado [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) objeto que representa o item de destino para o qual criar o objeto de interface.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-107">[in] A pointer to a user-implemented [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) object that represents the target item for which to create the interface object.</span></span>  
  
 `iface`  
 <span data-ttu-id="ca9b4-108">[out] Um ponteiro para o endereço do objeto retornado de interface.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-108">[out] A pointer to the address of the returned interface object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca9b4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca9b4-109">Remarks</span></span>  
 <span data-ttu-id="ca9b4-110">O `ICLRDataTarget` objeto é implementado pelo gerador do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-110">The `ICLRDataTarget` object is implemented by the writer of the debugging application.</span></span> <span data-ttu-id="ca9b4-111">A implementação depende do tipo de item de destino que está sendo representado.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-111">The implementation depends on the type of target item being represented.</span></span> <span data-ttu-id="ca9b4-112">O item de destino pode ser um processo, despejo de memória, computador remoto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="ca9b4-112">The target item may be a process, memory dump, remote machine, and so on.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca9b4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca9b4-113">Requirements</span></span>  
 <span data-ttu-id="ca9b4-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca9b4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca9b4-115">**Cabeçalho:** ClrData.idl</span><span class="sxs-lookup"><span data-stu-id="ca9b4-115">**Header:** ClrData.idl</span></span>  
  
 <span data-ttu-id="ca9b4-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca9b4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca9b4-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca9b4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca9b4-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca9b4-118">See Also</span></span>  
 [<span data-ttu-id="ca9b4-119">Depurando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="ca9b4-119">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
