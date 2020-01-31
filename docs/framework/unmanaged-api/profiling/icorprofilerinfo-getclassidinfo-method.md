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
ms.openlocfilehash: 4b9c577fab91e9527a1edc6c93e0618c8fe4e662
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864045"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="5b0fc-102">Método ICorProfilerInfo::GetClassIDInfo</span><span class="sxs-lookup"><span data-stu-id="5b0fc-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="5b0fc-103">Obtém o módulo pai e o token de metadados para a classe especificada.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b0fc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b0fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b0fc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b0fc-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5b0fc-106">no A ID da classe para a qual obter as informações.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="5b0fc-107">fora Um ponteiro para a ID do módulo pai da classe.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="5b0fc-108">fora Um ponteiro para o token de metadados para a classe.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b0fc-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b0fc-109">Remarks</span></span>  
 <span data-ttu-id="5b0fc-110">O código do criador de perfil pode chamar [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="5b0fc-111">O token de metadados que é retornado para o local referenciado por `pTypeDefToken` pode ser usado para acessar os metadados da classe.</span><span class="sxs-lookup"><span data-stu-id="5b0fc-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="5b0fc-112">Para obter mais informações sobre tipos genéricos, use [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="5b0fc-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b0fc-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="5b0fc-113">Requirements</span></span>  
 <span data-ttu-id="5b0fc-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b0fc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b0fc-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b0fc-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b0fc-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b0fc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b0fc-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b0fc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b0fc-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="5b0fc-118">See also</span></span>

- [<span data-ttu-id="5b0fc-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5b0fc-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
