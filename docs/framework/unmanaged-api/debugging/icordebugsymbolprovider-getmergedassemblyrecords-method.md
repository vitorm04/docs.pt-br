---
title: 'Método ICorDebugSymbolProvider:: GetMergedAssemblyRecords'
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 6a537a88bd4ab666eff8b5dda994da96bfcc5e52
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791618"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="af769-102">Método ICorDebugSymbolProvider:: GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="af769-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>
<span data-ttu-id="af769-103">Obtém os registros de símbolo de todos os assemblies mesclados.</span><span class="sxs-lookup"><span data-stu-id="af769-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af769-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af769-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af769-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="af769-105">Parameters</span></span>  
 `cRequestedRecords`  
 <span data-ttu-id="af769-106">no O número de registros de símbolo solicitado.</span><span class="sxs-lookup"><span data-stu-id="af769-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="af769-107">fora Um ponteiro para o número de registros de símbolo recuperados pelo método.</span><span class="sxs-lookup"><span data-stu-id="af769-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="af769-108">Um ponteiro para uma matriz de objetos [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="af769-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af769-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="af769-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af769-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="af769-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af769-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="af769-111">Requirements</span></span>  
 <span data-ttu-id="af769-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af769-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af769-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af769-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af769-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af769-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af769-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af769-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af769-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="af769-116">See also</span></span>

- [<span data-ttu-id="af769-117">Interface ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="af769-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="af769-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="af769-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
