---
title: Método ICorProfilerInfo::GetClassIDInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
ms.openlocfilehash: 4fbee938ae86b338f2beb0b48feeee46f144a4a0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498486"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="b3099-102">Método ICorProfilerInfo::GetClassIDInfo</span><span class="sxs-lookup"><span data-stu-id="b3099-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="b3099-103">Obtém o módulo pai e o token de metadados para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="b3099-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3099-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3099-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3099-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3099-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b3099-106">no A ID da classe para a qual obter as informações.</span><span class="sxs-lookup"><span data-stu-id="b3099-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b3099-107">fora Um ponteiro para a ID do módulo pai da classe.</span><span class="sxs-lookup"><span data-stu-id="b3099-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="b3099-108">fora Um ponteiro para o token de metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="b3099-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3099-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3099-109">Remarks</span></span>  
 <span data-ttu-id="b3099-110">O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="b3099-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="b3099-111">O token de metadados que é retornado para o local referenciado por `pTypeDefToken` pode ser usado para acessar os metadados da classe.</span><span class="sxs-lookup"><span data-stu-id="b3099-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="b3099-112">Para obter mais informações sobre tipos genéricos, use [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="b3099-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3099-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3099-113">Requirements</span></span>  
 <span data-ttu-id="b3099-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3099-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3099-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b3099-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3099-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3099-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3099-117">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3099-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3099-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="b3099-118">See also</span></span>

- [<span data-ttu-id="b3099-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b3099-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
