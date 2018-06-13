---
title: Ponteiro de função FExecuteInAppDomainCallback
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c3cafe3a8912702a093f9df7234112c0057b440
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431294"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="0c2cb-102">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="0c2cb-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="0c2cb-103">Aponta para uma função que é chamado pelo common language runtime (CLR) para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="0c2cb-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="0c2cb-104">Este ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0c2cb-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c2cb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c2cb-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c2cb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c2cb-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="0c2cb-107">[in] Um ponteiro para a memória alocada pelo chamador opaco que contém o código gerenciado para ser executado.</span><span class="sxs-lookup"><span data-stu-id="0c2cb-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="0c2cb-108">A alocação e a vida útil da memória são controladas pelo chamador (ou seja, o CLR).</span><span class="sxs-lookup"><span data-stu-id="0c2cb-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="0c2cb-109">Isso não é memória de heap gerenciado do CLR.</span><span class="sxs-lookup"><span data-stu-id="0c2cb-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c2cb-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c2cb-110">Requirements</span></span>  
 <span data-ttu-id="0c2cb-111">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c2cb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c2cb-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0c2cb-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c2cb-113">**Biblioteca:** arquivo MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="0c2cb-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="0c2cb-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c2cb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c2cb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c2cb-115">See Also</span></span>  
 [<span data-ttu-id="0c2cb-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="0c2cb-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
