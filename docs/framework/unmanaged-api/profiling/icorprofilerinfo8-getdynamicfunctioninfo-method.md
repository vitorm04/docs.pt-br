---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 90246ade67f797c04f0da5d9a68dadb83e4ce418
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973856"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a><span data-ttu-id="cd02f-102">Método ICorProfilerInfo8:: GetDynamicFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="cd02f-102">ICorProfilerInfo8::GetDynamicFunctionInfo Method</span></span>
  
 <span data-ttu-id="cd02f-103">Recupera informações sobre métodos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="cd02f-103">Retrieves information about dynamic methods.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="cd02f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd02f-104">Syntax</span></span>  
  
```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd02f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cd02f-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cd02f-106">no A ID da função para a qual recuperar informações.</span><span class="sxs-lookup"><span data-stu-id="cd02f-106">[in] The ID of the function for which to retrieve information.</span></span>  

 `moduleId`  
 <span data-ttu-id="cd02f-107">no Um ponteiro para o módulo no qual a classe pai da função é definida.</span><span class="sxs-lookup"><span data-stu-id="cd02f-107">[in] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="cd02f-108">fora Um ponteiro para a assinatura da função.</span><span class="sxs-lookup"><span data-stu-id="cd02f-108">[out] A pointer to the signature for the function.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="cd02f-109">fora Um ponteiro para a contagem de bytes para a assinatura de função.</span><span class="sxs-lookup"><span data-stu-id="cd02f-109">[out] A pointer to the count of bytes for the function signature.</span></span>
  
 `cchName`  
 <span data-ttu-id="cd02f-110">no O tamanho máximo da `wszName` matriz.</span><span class="sxs-lookup"><span data-stu-id="cd02f-110">[in] The maximum size of the `wszName` array.</span></span>
  
 `pcchName`  
 <span data-ttu-id="cd02f-111">fora O número de caracteres na `wszName` matriz.</span><span class="sxs-lookup"><span data-stu-id="cd02f-111">[out] The number of characters in the `wszName` array.</span></span>

 `wszName` \
 <span data-ttu-id="cd02f-112">fora Uma matriz `WCHAR` que é o nome da função, se existir uma.</span><span class="sxs-lookup"><span data-stu-id="cd02f-112">[out] An array of `WCHAR` which is the name of the function, if one exists.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="cd02f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd02f-113">Remarks</span></span>  
 <span data-ttu-id="cd02f-114">Determinados métodos, como stubs IL ou LCG, não têm metadados associados que podem ser recuperados usando as APIs [IMetaDataImport](../metadata/imetadataimport-interface.md) e [IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cd02f-114">Certain methods like IL Stubs or LCG do not have associated metadata that can be retrieved using the [IMetaDataImport](../metadata/imetadataimport-interface.md) and [IMetaDataImport2](../metadata/imetadataimport2-interface.md) APIs.</span></span> <span data-ttu-id="cd02f-115">Esses métodos podem ser encontrados por infilers por meio de ponteiros de instrução ou ouvindo [ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="cd02f-115">Such methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback8::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

 <span data-ttu-id="cd02f-116">Essa API pode ser usada para recuperar informações sobre métodos dinâmicos, incluindo um nome amigável, se disponível.</span><span class="sxs-lookup"><span data-stu-id="cd02f-116">This API can be used to retrieve information about dynamic methods, including a friendly name, if available.</span></span>  
  

## <a name="requirements"></a><span data-ttu-id="cd02f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd02f-117">Requirements</span></span>  
 <span data-ttu-id="cd02f-118">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd02f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd02f-119">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd02f-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd02f-120">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd02f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd02f-121">**.NET Framework versões:** [! INCLUIR[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="cd02f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd02f-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd02f-122">See also</span></span>
- [<span data-ttu-id="cd02f-123">Interface ICorProfilerInfo8</span><span class="sxs-lookup"><span data-stu-id="cd02f-123">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

