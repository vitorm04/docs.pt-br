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
ms.openlocfilehash: e1dd6addd9053ffb6cf2ce23408673d8fca17cb5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496835"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="11539-102">Método ICorProfilerInfo2::GetStaticFieldInfo</span><span class="sxs-lookup"><span data-stu-id="11539-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="11539-103">Obtém um valor que indica o tipo de estático que se aplica ao campo especificado.</span><span class="sxs-lookup"><span data-stu-id="11539-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11539-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="11539-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11539-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="11539-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="11539-106">no A ID da classe na qual o campo estático é definido.</span><span class="sxs-lookup"><span data-stu-id="11539-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="11539-107">no O token de metadados para o campo estático.</span><span class="sxs-lookup"><span data-stu-id="11539-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="11539-108">fora Um ponteiro para um valor da enumeração [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) que indica se o campo especificado é estático e, nesse caso, o tipo de estático que se aplica ao campo.</span><span class="sxs-lookup"><span data-stu-id="11539-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11539-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="11539-109">Remarks</span></span>  
 <span data-ttu-id="11539-110">Essas informações podem ser usadas para determinar qual função chamar para obter o endereço do campo estático.</span><span class="sxs-lookup"><span data-stu-id="11539-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="11539-111">O código do criador de perfil ainda deve verificar os metadados de um campo estático para garantir que ele realmente tenha um endereço.</span><span class="sxs-lookup"><span data-stu-id="11539-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="11539-112">Literais estáticos (ou seja, constantes) existem somente nos metadados e não têm um endereço.</span><span class="sxs-lookup"><span data-stu-id="11539-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11539-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="11539-113">Requirements</span></span>  
 <span data-ttu-id="11539-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11539-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11539-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11539-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11539-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11539-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11539-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11539-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11539-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="11539-118">See also</span></span>

- [<span data-ttu-id="11539-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="11539-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="11539-120">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="11539-120">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
