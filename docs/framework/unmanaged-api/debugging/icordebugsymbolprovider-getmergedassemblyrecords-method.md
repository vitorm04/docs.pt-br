---
title: 'Método ICorDebugSymbolProvider:: GetMergedAssemblyRecords'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6faf8960c06488c8fff5a076aae375529e1d0260
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138867"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="f7717-102">Método ICorDebugSymbolProvider:: GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="f7717-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="f7717-103">Obtém os registros de símbolo de todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="f7717-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7717-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7717-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7717-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7717-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="f7717-106">no O número de registros de símbolo solicitado.</span><span class="sxs-lookup"><span data-stu-id="f7717-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="f7717-107">fora Um ponteiro para o número de registros de símbolo recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="f7717-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="f7717-108">Um ponteiro para uma matriz de objetos [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f7717-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7717-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7717-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7717-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f7717-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7717-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7717-111">Requirements</span></span>  
 <span data-ttu-id="f7717-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7717-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7717-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7717-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7717-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7717-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7717-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7717-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7717-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7717-116">See also</span></span>

- [<span data-ttu-id="f7717-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="f7717-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f7717-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="f7717-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
