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
ms.openlocfilehash: 841953625235406f013e9f140ad91c7b65680e47
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863947"
---
# <a name="icorprofilerinfogetclassfromtoken-method"></a><span data-ttu-id="22501-102">Método ICorProfilerInfo::GetClassFromToken</span><span class="sxs-lookup"><span data-stu-id="22501-102">ICorProfilerInfo::GetClassFromToken Method</span></span>
<span data-ttu-id="22501-103">Obtém a ID da classe, dado o token de metadados.</span><span class="sxs-lookup"><span data-stu-id="22501-103">Gets the ID of the class, given the metadata token.</span></span> <span data-ttu-id="22501-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="22501-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="22501-105">Use [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="22501-105">Use [ICorProfilerInfo2::GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22501-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22501-106">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromToken(  
    [in]  ModuleID  moduleId,  
    [in]  mdTypeDef typeDef,  
    [out] ClassID   *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22501-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22501-107">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="22501-108">no A ID do módulo que contém a classe.</span><span class="sxs-lookup"><span data-stu-id="22501-108">[in] The ID of the module that contains the class.</span></span>  
  
 `typeDef`  
 <span data-ttu-id="22501-109">no Um `mdTypeDef` token de metadados que faz referência à classe.</span><span class="sxs-lookup"><span data-stu-id="22501-109">[in] An `mdTypeDef` metadata token that references the class.</span></span>  
  
 `cTypeArgs`  
 <span data-ttu-id="22501-110">fora Um ponteiro para a ID de classe.</span><span class="sxs-lookup"><span data-stu-id="22501-110">[out] A pointer to the class ID.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22501-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="22501-111">Remarks</span></span>  
 <span data-ttu-id="22501-112">Este método é obsoleto; em vez disso, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` para todos os tipos.</span><span class="sxs-lookup"><span data-stu-id="22501-112">This method is obsolete; instead, use `ICorProfilerInfo2::GetClassFromTokenAndTypeArgs` for all types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22501-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="22501-113">Requirements</span></span>  
 <span data-ttu-id="22501-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22501-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22501-115">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="22501-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22501-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22501-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22501-117">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="22501-117">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22501-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="22501-118">See also</span></span>

- [<span data-ttu-id="22501-119">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="22501-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
