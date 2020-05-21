---
title: Método ICorRuntimeHost::Start
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: ccad76e1c8a49222d4f527f8b7b18d4e40ff8cae
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760401"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="bd8e9-102">Método ICorRuntimeHost::Start</span><span class="sxs-lookup"><span data-stu-id="bd8e9-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="bd8e9-103">Inicia o Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bd8e9-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8e9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd8e9-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bd8e9-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bd8e9-105">Return Value</span></span>  
  
|<span data-ttu-id="bd8e9-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bd8e9-106">HRESULT</span></span>|<span data-ttu-id="bd8e9-107">Description</span><span class="sxs-lookup"><span data-stu-id="bd8e9-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bd8e9-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bd8e9-108">S_OK</span></span>|<span data-ttu-id="bd8e9-109">A operação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-109">The operation was successful.</span></span>|  
|<span data-ttu-id="bd8e9-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bd8e9-110">S_FALSE</span></span>|<span data-ttu-id="bd8e9-111">Falha ao concluir a operação.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="bd8e9-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bd8e9-112">E_FAIL</span></span>|<span data-ttu-id="bd8e9-113">Ocorreu uma falha catastrófica desconhecida.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="bd8e9-114">Se um método retornar E_FAIL, o CLR não poderá mais ser usado no processo.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="bd8e9-115">As chamadas subsequentes para qualquer API de hospedagem retornam HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bd8e9-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bd8e9-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bd8e9-117">O CLR não foi carregado em um processo ou o CLR está em um estado no qual não pode executar código gerenciado ou processar a chamada com êxito.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8e9-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd8e9-118">Remarks</span></span>  
 <span data-ttu-id="bd8e9-119">Normalmente, não é necessário chamar o `Start` método, porque o CLR inicia automaticamente na primeira solicitação para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bd8e9-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8e9-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bd8e9-120">Requirements</span></span>  
 <span data-ttu-id="bd8e9-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd8e9-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd8e9-122">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bd8e9-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bd8e9-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bd8e9-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bd8e9-124">**Versões do .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="bd8e9-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8e9-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="bd8e9-125">See also</span></span>

- [<span data-ttu-id="bd8e9-126">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="bd8e9-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
