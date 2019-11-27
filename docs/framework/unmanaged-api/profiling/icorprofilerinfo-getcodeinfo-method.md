---
title: Método ICorProfilerInfo::GetCodeInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: 2393468f78312511d11cbe0ab422c26c710e25d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439231"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="f7837-102">Método ICorProfilerInfo::GetCodeInfo</span><span class="sxs-lookup"><span data-stu-id="f7837-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="f7837-103">Obtém a extensão do código nativo associado à ID da função especificada.</span><span class="sxs-lookup"><span data-stu-id="f7837-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="f7837-104">Esse método é obsoleto.</span><span class="sxs-lookup"><span data-stu-id="f7837-104">This method is obsolete.</span></span> <span data-ttu-id="f7837-105">Em vez disso, use o método [ICorProfilerInfo2:: GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f7837-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7837-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7837-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7837-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7837-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f7837-108">no A ID da função à qual o código nativo está associado.</span><span class="sxs-lookup"><span data-stu-id="f7837-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="f7837-109">fora Um ponteiro para uma matriz de bytes que compõe o código nativo da função.</span><span class="sxs-lookup"><span data-stu-id="f7837-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f7837-110">fora Um ponteiro para um inteiro que especifica o tamanho, em bytes, do código nativo.</span><span class="sxs-lookup"><span data-stu-id="f7837-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7837-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7837-111">Remarks</span></span>  
 <span data-ttu-id="f7837-112">Para otimizar o desempenho, o tempo de execução na versão 2,0 do .NET Framework divide o código pré-compilado precompilado de uma função em várias regiões.</span><span class="sxs-lookup"><span data-stu-id="f7837-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="f7837-113">Consequentemente, o método `GetCodeInfo` é obsoleto no .NET Framework 2,0 porque não é possível manipular a extensão do código nativo de uma função.</span><span class="sxs-lookup"><span data-stu-id="f7837-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="f7837-114">Os profileres devem mudar para o uso do método mais geral `ICorProfilerInfo2::GetCodeInfo2` em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f7837-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="f7837-115">Essa função usa buffers alocados pelo chamador.</span><span class="sxs-lookup"><span data-stu-id="f7837-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7837-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f7837-116">Requirements</span></span>  
 <span data-ttu-id="f7837-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7837-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7837-118">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f7837-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7837-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7837-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7837-120">**Versões do .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="f7837-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7837-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f7837-121">See also</span></span>

- [<span data-ttu-id="f7837-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f7837-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f7837-123">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f7837-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f7837-124">Criação de perfil</span><span class="sxs-lookup"><span data-stu-id="f7837-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
