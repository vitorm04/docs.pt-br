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
ms.openlocfilehash: 6fd7a19d9fc77b43bbceb1b5e5399a455429e700
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616145"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="449a5-102">Ponteiro de função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="449a5-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="449a5-103">Aponta para uma função que é chamada pelo Common Language Runtime (CLR) para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="449a5-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="449a5-104">Esse ponteiro de função foi preterido no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="449a5-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="449a5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="449a5-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="449a5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="449a5-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="449a5-107">no Um ponteiro para uma memória opaca alocada pelo chamador que contém o código gerenciado a ser executado.</span><span class="sxs-lookup"><span data-stu-id="449a5-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="449a5-108">A alocação e o tempo de vida dessa memória são controlados pelo chamador (ou seja, o CLR).</span><span class="sxs-lookup"><span data-stu-id="449a5-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="449a5-109">Essa não é uma memória de heap gerenciada pelo CLR.</span><span class="sxs-lookup"><span data-stu-id="449a5-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="449a5-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="449a5-110">Requirements</span></span>  
 <span data-ttu-id="449a5-111">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="449a5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="449a5-112">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="449a5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="449a5-113">**Biblioteca:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="449a5-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="449a5-114">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="449a5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449a5-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="449a5-115">See also</span></span>

- [<span data-ttu-id="449a5-116">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="449a5-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
