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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a74e99e0b669c1b3d8e36d881391f27ef71ae306
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493538"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="d43ca-102">Método ICorProfilerInfo::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="d43ca-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="d43ca-103">Obtém a ID da classe, considerando o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="d43ca-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="d43ca-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="d43ca-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="d43ca-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d43ca-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43ca-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d43ca-106">Syntax</span></span>  
  
```  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d43ca-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d43ca-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="d43ca-108">[in] A ID do módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="d43ca-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="d43ca-109">[in] Um `mdTypeDef` token de metadados que faz referência à classe.</span><span class="sxs-lookup"><span data-stu-id="d43ca-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="d43ca-110">[out] Um ponteiro para a ID de classe.</span><span class="sxs-lookup"><span data-stu-id="d43ca-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d43ca-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="d43ca-111">Remarks</span></span>  
 <span data-ttu-id="d43ca-112">Este método é obsoleto; em vez disso, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="d43ca-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43ca-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d43ca-113">Requirements</span></span>  
 <span data-ttu-id="d43ca-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d43ca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43ca-115">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d43ca-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d43ca-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d43ca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d43ca-117">**Versões do .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d43ca-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43ca-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d43ca-118">See also</span></span>
- [<span data-ttu-id="d43ca-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d43ca-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
