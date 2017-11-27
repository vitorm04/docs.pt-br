---
title: "Método ICorDebugAssemblyEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssemblyEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssemblyEnum::Next method
helpviewer_keywords:
- ICorDebugAssemblyEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: b3e7d0c2-3baa-4ef8-8e3f-b865cf252940
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7430a420769a2d7952caf93af3b1412094483f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugassemblyenumnext-method"></a><span data-ttu-id="9397b-102">Método ICorDebugAssemblyEnum::Next</span><span class="sxs-lookup"><span data-stu-id="9397b-102">ICorDebugAssemblyEnum::Next Method</span></span>
<span data-ttu-id="9397b-103">Obtém o número especificado de assemblies da coleção, começando na posição atual do cursor.</span><span class="sxs-lookup"><span data-stu-id="9397b-103">Gets the specified number of assemblies from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9397b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9397b-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugAssembly *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9397b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9397b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9397b-106">[in] O número de módulos (assemblies) a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="9397b-106">[in] The number of assemblies to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="9397b-107">[out] Uma matriz de ponteiros, cada um deles aponta para um objeto ICorDebugAssembly que representa um assembly.</span><span class="sxs-lookup"><span data-stu-id="9397b-107">[out] An array of pointers, each of which points to an ICorDebugAssembly object that represents an assembly.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9397b-108">[out] Um ponteiro para o número de assemblies de fato retornadas.</span><span class="sxs-lookup"><span data-stu-id="9397b-108">[out] A pointer to the number of assemblies actually returned.</span></span> <span data-ttu-id="9397b-109">Esse valor pode ser null se `celt` é um.</span><span class="sxs-lookup"><span data-stu-id="9397b-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9397b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9397b-110">Requirements</span></span>  
 <span data-ttu-id="9397b-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9397b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9397b-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9397b-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9397b-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9397b-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9397b-114">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9397b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
