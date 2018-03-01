---
title: "Método ICorDebugAssembly::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugAssembly.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetName
helpviewer_keywords:
- ICorDebugAssembly::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: cdeda721-b214-4503-a291-c70b68b5f36b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cf2b84a6ab7cc1745fbf7330e66f94ea04635892
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetname-method"></a><span data-ttu-id="2360a-102">Método ICorDebugAssembly::GetName</span><span class="sxs-lookup"><span data-stu-id="2360a-102">ICorDebugAssembly::GetName Method</span></span>
<span data-ttu-id="2360a-103">Obtém o nome do assembly que isso `ICorDebugAssembly` instância representa.</span><span class="sxs-lookup"><span data-stu-id="2360a-103">Gets the name of the assembly that this `ICorDebugAssembly` instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2360a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2360a-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32  cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2360a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2360a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2360a-106">[in] O tamanho do `szName` matriz.</span><span class="sxs-lookup"><span data-stu-id="2360a-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2360a-107">[out] Um ponteiro para um inteiro que especifica o comprimento real do nome.</span><span class="sxs-lookup"><span data-stu-id="2360a-107">[out] A pointer to an integer that specifies the actual length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="2360a-108">[out] Uma matriz que armazena o nome.</span><span class="sxs-lookup"><span data-stu-id="2360a-108">[out] An array that stores the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2360a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2360a-109">Remarks</span></span>  
 <span data-ttu-id="2360a-110">O `GetName` método retorna o nome de arquivo e caminho completo do assembly.</span><span class="sxs-lookup"><span data-stu-id="2360a-110">The `GetName` method returns the full path and file name of the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2360a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2360a-111">Requirements</span></span>  
 <span data-ttu-id="2360a-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2360a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2360a-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2360a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2360a-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2360a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2360a-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2360a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
