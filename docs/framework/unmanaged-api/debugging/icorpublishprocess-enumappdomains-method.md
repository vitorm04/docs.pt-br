---
title: Método ICorPublishProcess::EnumAppDomains
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.EnumAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::EnumAppDomains
helpviewer_keywords:
- EnumAppDomains method [.NET Framework debugging]
- ICorPublishProcess::EnumAppDomains method [.NET Framework debugging]
ms.assetid: 7da621fc-e7d0-4c00-9439-5c93619d7414
topic_type:
- apiref
ms.openlocfilehash: 4799c1d04e8172c604eeec50f2b841a6db063949
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790579"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="a9585-102">Método ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="a9585-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="a9585-103">Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a9585-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9585-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a9585-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9585-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a9585-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a9585-106">fora Um ponteiro para o endereço de uma instância de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) que permite a iteração por meio da coleção de domínios de aplicativo nesse processo.</span><span class="sxs-lookup"><span data-stu-id="a9585-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9585-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="a9585-107">Remarks</span></span>  
 <span data-ttu-id="a9585-108">A lista de domínios de aplicativo é baseada em um instantâneo dos domínios de aplicativo que existem quando o método de `EnumAppDomains` é chamado.</span><span class="sxs-lookup"><span data-stu-id="a9585-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="a9585-109">Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada.</span><span class="sxs-lookup"><span data-stu-id="a9585-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="a9585-110">As listas existentes não serão afetadas pelas chamadas subsequentes desse método.</span><span class="sxs-lookup"><span data-stu-id="a9585-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="a9585-111">Se o processo tiver sido encerrado, `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="a9585-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9585-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="a9585-112">Requirements</span></span>  
 <span data-ttu-id="a9585-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9585-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9585-114">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="a9585-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="a9585-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9585-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9585-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9585-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9585-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="a9585-117">See also</span></span>

- [<span data-ttu-id="a9585-118">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="a9585-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
