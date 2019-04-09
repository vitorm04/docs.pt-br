---
title: Método ICorDebugThread::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa90aff73d94baf2cbf7d01f41710cb2aa10213
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178731"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="f4626-102">Método ICorDebugThread::GetObject</span><span class="sxs-lookup"><span data-stu-id="f4626-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="f4626-103">Obtém um ponteiro de interface para o thread comum a language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="f4626-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4626-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f4626-104">Syntax</span></span>  
  
```  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4626-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f4626-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="f4626-106">[out] Um ponteiro para o endereço de um objeto de interface ICorDebugValue que representa o thread CLR.</span><span class="sxs-lookup"><span data-stu-id="f4626-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4626-107">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f4626-107">Requirements</span></span>  
 <span data-ttu-id="f4626-108">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4626-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4626-109">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4626-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4626-110">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4626-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f4626-111">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f4626-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4626-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f4626-112">See also</span></span>

- <xref:System.Threading.Thread>
