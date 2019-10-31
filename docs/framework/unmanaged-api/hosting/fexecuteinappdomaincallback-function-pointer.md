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
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138177"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="8aafe-102">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="8aafe-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="8aafe-103">Aponta para uma função que é chamada pelo Common Language Runtime (CLR) para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8aafe-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="8aafe-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8aafe-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aafe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8aafe-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aafe-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8aafe-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="8aafe-107">no Um ponteiro para uma memória opaca alocada pelo chamador que contém o código gerenciado a ser executado.</span><span class="sxs-lookup"><span data-stu-id="8aafe-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="8aafe-108">A alocação e o tempo de vida dessa memória são controlados pelo chamador (ou seja, o CLR).</span><span class="sxs-lookup"><span data-stu-id="8aafe-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="8aafe-109">Essa não é uma memória de heap gerenciada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="8aafe-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aafe-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8aafe-110">Requirements</span></span>  
 <span data-ttu-id="8aafe-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aafe-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aafe-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8aafe-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8aafe-113">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="8aafe-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="8aafe-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aafe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aafe-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8aafe-115">See also</span></span>

- [<span data-ttu-id="8aafe-116">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8aafe-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
