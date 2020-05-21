---
title: Método ICorRuntimeHost::LocksHeldByLogicalThread
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
ms.openlocfilehash: 265ab5ae03b7b42c4f5f429df5d659d60e55f18e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760713"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="c79af-102">Método ICorRuntimeHost::LocksHeldByLogicalThread</span><span class="sxs-lookup"><span data-stu-id="c79af-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="c79af-103">Recupera o número de bloqueios que o thread atual mantém.</span><span class="sxs-lookup"><span data-stu-id="c79af-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="c79af-104">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="c79af-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79af-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c79af-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c79af-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c79af-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="c79af-107">fora Um ponteiro para o número de bloqueios que o thread atual mantém.</span><span class="sxs-lookup"><span data-stu-id="c79af-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c79af-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c79af-108">Requirements</span></span>  
 <span data-ttu-id="c79af-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c79af-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c79af-110">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c79af-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c79af-111">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c79af-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c79af-112">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c79af-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79af-113">Veja também</span><span class="sxs-lookup"><span data-stu-id="c79af-113">See also</span></span>

- [<span data-ttu-id="c79af-114">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c79af-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
