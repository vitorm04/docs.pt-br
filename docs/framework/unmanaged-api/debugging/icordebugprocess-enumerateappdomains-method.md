---
title: Método ICorDebugProcess::EnumerateAppDomains
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: 35e3e37b1487b5dda9945402c6a3338384147f9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792634"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="8c944-102">Método ICorDebugProcess::EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="8c944-102">ICorDebugProcess::EnumerateAppDomains Method</span></span>
<span data-ttu-id="8c944-103">Enumera todos os domínios de aplicativo neste processo.</span><span class="sxs-lookup"><span data-stu-id="8c944-103">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c944-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c944-104">Syntax</span></span>  
  
``` cpp 
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c944-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c944-105">Parameters</span></span>  
 `ppAppDomains`  
 <span data-ttu-id="8c944-106">fora Um ponteiro para o endereço de um [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) que é um enumerador para os domínios de aplicativo nesse processo.</span><span class="sxs-lookup"><span data-stu-id="8c944-106">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c944-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8c944-107">Remarks</span></span>  
 <span data-ttu-id="8c944-108">Esse método pode ser usado antes do retorno de chamada [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8c944-108">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c944-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="8c944-109">Requirements</span></span>  
 <span data-ttu-id="8c944-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c944-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c944-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8c944-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8c944-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8c944-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c944-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c944-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
