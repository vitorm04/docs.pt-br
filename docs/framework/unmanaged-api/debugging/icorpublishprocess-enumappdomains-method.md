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
ms.openlocfilehash: 0c3b5da52b78150198fa9f910bf01b4657e4eba8
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421157"
---
# <a name="icorpublishprocessenumappdomains-method"></a><span data-ttu-id="29710-102">Método ICorPublishProcess::EnumAppDomains</span><span class="sxs-lookup"><span data-stu-id="29710-102">ICorPublishProcess::EnumAppDomains Method</span></span>
<span data-ttu-id="29710-103">Obtém um enumerador para os domínios de aplicativo no processo que é referenciado por este [ICorPublishProcess](icorpublishprocess-interface.md).</span><span class="sxs-lookup"><span data-stu-id="29710-103">Gets an enumerator for the application domains in the process that is referenced by this [ICorPublishProcess](icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29710-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29710-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAppDomains (  
    [out] ICorPublishAppDomainEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29710-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29710-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="29710-106">fora Um ponteiro para o endereço de uma instância de [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) que permite a iteração por meio da coleção de domínios de aplicativo nesse processo.</span><span class="sxs-lookup"><span data-stu-id="29710-106">[out] A pointer to the address of an [ICorPublishAppDomainEnum](icorpublishappdomainenum-interface.md) instance that allows iteration through the collection of application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29710-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="29710-107">Remarks</span></span>  
 <span data-ttu-id="29710-108">A lista de domínios de aplicativo é baseada em um instantâneo dos domínios de aplicativo que existem quando o `EnumAppDomains` método é chamado.</span><span class="sxs-lookup"><span data-stu-id="29710-108">The list of application domains is based on a snapshot of the application domains that exist when the `EnumAppDomains` method is called.</span></span> <span data-ttu-id="29710-109">Esse método pode ser chamado mais de uma vez para criar uma nova lista atualizada.</span><span class="sxs-lookup"><span data-stu-id="29710-109">This method may be called more than once to create a new up-to-date list.</span></span> <span data-ttu-id="29710-110">As listas existentes não serão afetadas pelas chamadas subsequentes desse método.</span><span class="sxs-lookup"><span data-stu-id="29710-110">Existing lists will not be affected by subsequent calls of this method.</span></span>  
  
 <span data-ttu-id="29710-111">Se o processo tiver sido encerrado, o `EnumAppDomains` falhará com um valor HRESULT de CORDBG_E_PROCESS_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="29710-111">If the process has been terminated, `EnumAppDomains` will fail with an HRESULT value of CORDBG_E_PROCESS_TERMINATED.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29710-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29710-112">Requirements</span></span>  
 <span data-ttu-id="29710-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29710-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29710-114">**Cabeçalho:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="29710-114">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29710-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29710-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29710-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29710-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29710-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="29710-117">See also</span></span>

- [<span data-ttu-id="29710-118">Interface ICorPublishProcess</span><span class="sxs-lookup"><span data-stu-id="29710-118">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
