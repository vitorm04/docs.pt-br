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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c614afee18824e1672b378dd468cb11c9c173d9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764951"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="5b738-102">Método ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="5b738-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="5b738-103">Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="5b738-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b738-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b738-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b738-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b738-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="5b738-106">[out] Um ponteiro para o endereço de um [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que permite iteração por meio da coleção de domínios de aplicativo nesse processo.</span><span class="sxs-lookup"><span data-stu-id="5b738-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b738-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b738-107">Remarks</span></span>  
 <span data-ttu-id="5b738-108">A lista de domínios de aplicativo baseia-se em um instantâneo dos domínios de aplicativo existe quando o `EnumAppDomains` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="5b738-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="5b738-109">Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada.</span><span class="sxs-lookup"><span data-stu-id="5b738-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="5b738-110">Listas existentes não serão afetadas por chamadas subsequentes desse método.</span><span class="sxs-lookup"><span data-stu-id="5b738-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="5b738-111">Se o processo foi encerrado, `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="5b738-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b738-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b738-112">Requirements</span></span>  
 <span data-ttu-id="5b738-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b738-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b738-114">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="5b738-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5b738-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b738-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b738-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b738-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b738-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b738-117">See also</span></span>

- [<span data-ttu-id="5b738-118">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="5b738-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
