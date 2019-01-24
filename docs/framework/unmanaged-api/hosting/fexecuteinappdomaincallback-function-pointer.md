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
ms.openlocfilehash: e3031ce0eb6f23fdf5e5366d33ff075ea7816b0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649538"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="9fd5d-102">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="9fd5d-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="9fd5d-103">Aponta para uma função que é chamado pelo common language runtime (CLR) para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9fd5d-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="9fd5d-104">Esse ponteiro de função foi preterido no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fd5d-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd5d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fd5d-105">Syntax</span></span>  
  
```  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fd5d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fd5d-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="9fd5d-107">[in] Um ponteiro para a memória alocada pelo chamador opaco que contém o código gerenciado a ser executado.</span><span class="sxs-lookup"><span data-stu-id="9fd5d-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="9fd5d-108">A alocação e o tempo de vida da memória são controlados pelo chamador (ou seja, o CLR).</span><span class="sxs-lookup"><span data-stu-id="9fd5d-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="9fd5d-109">Isso não é a memória de heap gerenciado do CLR.</span><span class="sxs-lookup"><span data-stu-id="9fd5d-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fd5d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fd5d-110">Requirements</span></span>  
 <span data-ttu-id="9fd5d-111">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fd5d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fd5d-112">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fd5d-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fd5d-113">**Biblioteca:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="9fd5d-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="9fd5d-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fd5d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd5d-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fd5d-115">See also</span></span>
- [<span data-ttu-id="9fd5d-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="9fd5d-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
