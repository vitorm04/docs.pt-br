---
title: Método ICorProfilerInfo::GetClassFromToken
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromToken
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromToken
helpviewer_keywords:
- ICorProfilerInfo::GetClassFromToken method [.NET Framework profiling]
- GetClassFromToken method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 0afc1197-2a5b-424f-8b82-9cb59a7e00db
topic_type:
- apiref
ms.openlocfilehash: 6999821412b3cdd614cb30858a0616c9f27a6baa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448113"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="5d4c2-102">Método ICorProfilerInfo::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="5d4c2-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="5d4c2-103">Obtém a ID da classe, dado o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="5d4c2-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="5d4c2-105">Use [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d4c2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d4c2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d4c2-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d4c2-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="5d4c2-108">no A ID do módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="5d4c2-109">no Um `mdTypeDef` token de metadados que faz referência à classe.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="5d4c2-110">fora Um ponteiro para a ID de classe.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d4c2-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d4c2-111">Remarks</span></span>  
 <span data-ttu-id="5d4c2-112">Este método é obsoleto; em vez disso, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="5d4c2-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d4c2-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d4c2-113">Requirements</span></span>  
 <span data-ttu-id="5d4c2-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d4c2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d4c2-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d4c2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d4c2-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d4c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d4c2-117">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5d4c2-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4c2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d4c2-118">See also</span></span>

- [<span data-ttu-id="5d4c2-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="5d4c2-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
