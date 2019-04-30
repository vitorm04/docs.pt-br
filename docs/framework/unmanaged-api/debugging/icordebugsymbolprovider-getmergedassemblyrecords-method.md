---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords Method
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9003482860e554049c39ea9ffed4c52345bfeff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953303"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="5cff3-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span><span class="sxs-lookup"><span data-stu-id="5cff3-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="5cff3-103">Obtém os registros de símbolo para todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="5cff3-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cff3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cff3-104">Syntax</span></span>  
  
```  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cff3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5cff3-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="5cff3-106">[in] O número de registros de símbolo solicitado.</span><span class="sxs-lookup"><span data-stu-id="5cff3-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="5cff3-107">[out] Um ponteiro para o número de registros de símbolo recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="5cff3-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="5cff3-108">Um ponteiro para uma matriz de [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="5cff3-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cff3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cff3-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5cff3-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5cff3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cff3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cff3-111">Requirements</span></span>  
 <span data-ttu-id="5cff3-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cff3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cff3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cff3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cff3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cff3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cff3-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cff3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cff3-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cff3-116">See also</span></span>

- [<span data-ttu-id="5cff3-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="5cff3-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5cff3-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5cff3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
