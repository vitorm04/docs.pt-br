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
ms.openlocfilehash: 5492d4e1245c6c0ce5c1eb98d25168c5d69d123b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423696"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="9a009-102">Método ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="9a009-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="9a009-103">Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9a009-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a009-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a009-104">Syntax</span></span>  
  
```  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a009-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a009-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="9a009-106">[out] Um ponteiro para o endereço de um [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instância que permite iteração através da coleção de domínios do aplicativo neste processo.</span><span class="sxs-lookup"><span data-stu-id="9a009-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a009-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9a009-107">Remarks</span></span>  
 <span data-ttu-id="9a009-108">A lista de domínios de aplicativo é baseada em um instantâneo dos domínios de aplicativo existe quando o `EnumAppDomains` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="9a009-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="9a009-109">Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada.</span><span class="sxs-lookup"><span data-stu-id="9a009-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="9a009-110">Listas existentes não serão afetadas por chamadas subsequentes desse método.</span><span class="sxs-lookup"><span data-stu-id="9a009-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="9a009-111">Se o processo foi encerrado, `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="9a009-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a009-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9a009-112">Requirements</span></span>  
 <span data-ttu-id="9a009-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a009-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a009-114">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9a009-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9a009-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a009-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a009-116">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a009-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a009-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a009-117">See Also</span></span>  
 [<span data-ttu-id="9a009-118">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="9a009-118">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
