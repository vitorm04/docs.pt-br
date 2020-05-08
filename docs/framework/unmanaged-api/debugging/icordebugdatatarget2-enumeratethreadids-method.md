---
title: Método ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 4a65b76f384cdad68cba75af524dbe672c309624
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976480"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="860e7-102">Método ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="860e7-102">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>
<span data-ttu-id="860e7-103">Retorna uma lista de IDs de thread ativo.</span><span class="sxs-lookup"><span data-stu-id="860e7-103">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860e7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="860e7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="860e7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="860e7-105">Parameters</span></span>  
 <span data-ttu-id="860e7-106">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="860e7-106">cThreadIDs</span></span>  
 <span data-ttu-id="860e7-107">[in] O número máximo de threads cujos IDs podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="860e7-107">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="860e7-108">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="860e7-108">pcThreadIds</span></span>  
 <span data-ttu-id="860e7-109">[out] Um ponteiro para um `ULONG32` que indica o número real de IDs de thread gravadas na matriz `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="860e7-109">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="860e7-110">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="860e7-110">pThreadIDs</span></span>  
 <span data-ttu-id="860e7-111">Uma matriz de identificadores de thread.</span><span class="sxs-lookup"><span data-stu-id="860e7-111">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="860e7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="860e7-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="860e7-113">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="860e7-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860e7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="860e7-114">Requirements</span></span>  
 <span data-ttu-id="860e7-115">**Plataformas:** Consulte [requisitos do sistema](../../get-started/system-requirements.md). **Cabeçalho:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="860e7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="860e7-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="860e7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="860e7-117">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860e7-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860e7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="860e7-118">See also</span></span>

- [<span data-ttu-id="860e7-119">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="860e7-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="860e7-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="860e7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
