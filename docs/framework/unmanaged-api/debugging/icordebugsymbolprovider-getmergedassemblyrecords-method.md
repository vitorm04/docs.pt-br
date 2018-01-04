---
title: "Método ICorDebugSymbolProvider::GetMergedAssemblyRecords"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75c8a98b4e7b2e3250adfb75a5d2dcb29a71ff27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="fdb03-102">Método ICorDebugSymbolProvider::GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="fdb03-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="fdb03-103">Obtém os registros de símbolo para todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="fdb03-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb03-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fdb03-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fdb03-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fdb03-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="fdb03-106">[in] O número de registros de símbolo solicitado.</span><span class="sxs-lookup"><span data-stu-id="fdb03-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="fdb03-107">[out] Um ponteiro para o número de registros de símbolo recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="fdb03-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="fdb03-108">Um ponteiro para uma matriz de [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="fdb03-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdb03-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fdb03-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdb03-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fdb03-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb03-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fdb03-111">Requirements</span></span>  
 <span data-ttu-id="fdb03-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb03-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb03-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdb03-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdb03-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdb03-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdb03-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb03-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb03-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fdb03-116">See Also</span></span>  
 [<span data-ttu-id="fdb03-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="fdb03-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="fdb03-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="fdb03-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
