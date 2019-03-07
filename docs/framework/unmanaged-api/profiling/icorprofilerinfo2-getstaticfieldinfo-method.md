---
title: Método ICorProfilerInfo2::GetStaticFieldInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b17323b6e26bb7aa1413f87f9136adca8935b10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482737"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="200bb-102">Método ICorProfilerInfo2::GetStaticFieldInfo</span><span class="sxs-lookup"><span data-stu-id="200bb-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="200bb-103">Obtém um valor que indica o tipo de estático que se aplica ao campo especificado.</span><span class="sxs-lookup"><span data-stu-id="200bb-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="200bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="200bb-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="200bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="200bb-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="200bb-106">[in] A ID da classe no qual o campo estático é definido.</span><span class="sxs-lookup"><span data-stu-id="200bb-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="200bb-107">[in] O token de metadados para o campo estático.</span><span class="sxs-lookup"><span data-stu-id="200bb-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="200bb-108">[out] Um ponteiro para um valor igual a [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeração que indica se o campo especificado é estático e, se assim, o tipo de estático que se aplica ao campo.</span><span class="sxs-lookup"><span data-stu-id="200bb-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="200bb-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="200bb-109">Remarks</span></span>  
 <span data-ttu-id="200bb-110">Essas informações podem ser usadas para determinar qual função a ser chamada para obter o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="200bb-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="200bb-111">O código do criador de perfil ainda deve verificar os metadados para um campo estático para garantir que ele realmente tenha um endereço.</span><span class="sxs-lookup"><span data-stu-id="200bb-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="200bb-112">Literais estáticas (ou seja, constantes) existem somente nos metadados e não tem um endereço.</span><span class="sxs-lookup"><span data-stu-id="200bb-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="200bb-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="200bb-113">Requirements</span></span>  
 <span data-ttu-id="200bb-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="200bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="200bb-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="200bb-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="200bb-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="200bb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="200bb-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="200bb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="200bb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="200bb-118">See also</span></span>
- [<span data-ttu-id="200bb-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="200bb-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="200bb-120">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="200bb-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
