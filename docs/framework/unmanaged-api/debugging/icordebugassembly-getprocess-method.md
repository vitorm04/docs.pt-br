---
title: "Método ICorDebugAssembly::GetProcess"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly.GetProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fbb62bb6d2731c5bc2618de0a71f75e0979808c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="b21b4-102">Método ICorDebugAssembly::GetProcess</span><span class="sxs-lookup"><span data-stu-id="b21b4-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="b21b4-103">Obtém um ponteiro de interface para o processo no qual essa instância ICorDebugAssembly está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="b21b4-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b21b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b21b4-104">Syntax</span></span>  
  
```  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b21b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b21b4-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="b21b4-106">[out] Um ponteiro para uma interface ICorDebugProcess que representa o processo.</span><span class="sxs-lookup"><span data-stu-id="b21b4-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b21b4-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b21b4-107">Requirements</span></span>  
 <span data-ttu-id="b21b4-108">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b21b4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b21b4-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b21b4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b21b4-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b21b4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b21b4-111">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b21b4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
