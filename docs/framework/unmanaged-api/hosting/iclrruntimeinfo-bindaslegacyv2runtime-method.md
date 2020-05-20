---
title: Método ICLRRuntimeInfo::BindAsLegacyV2Runtime
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703898"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="c6050-102">Método ICLRRuntimeInfo::BindAsLegacyV2Runtime</span><span class="sxs-lookup"><span data-stu-id="c6050-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="c6050-103">Associa o tempo de execução atual a todas as decisões de política de ativação da versão 2 do Common Language Runtime herdado (CLR).</span><span class="sxs-lookup"><span data-stu-id="c6050-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6050-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6050-104">Syntax</span></span>  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c6050-105">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c6050-105">Return Value</span></span>  
 <span data-ttu-id="c6050-106">Esse método retorna os HRESULTs específicos a seguir:</span><span class="sxs-lookup"><span data-stu-id="c6050-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="c6050-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6050-107">HRESULT</span></span>|<span data-ttu-id="c6050-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="c6050-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6050-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6050-109">S_OK</span></span>|<span data-ttu-id="c6050-110">A associação foi bem-sucedida ou esse tempo de execução já estava associado ao tempo de execução da política de ativação do CLR versão 2 herdado.</span><span class="sxs-lookup"><span data-stu-id="c6050-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="c6050-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="c6050-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="c6050-112">Um tempo de execução diferente já estava associado à política de ativação do CLR versão 2 herdada.</span><span class="sxs-lookup"><span data-stu-id="c6050-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6050-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6050-113">Remarks</span></span>  
 <span data-ttu-id="c6050-114">Se o tempo de execução atual já estiver associado a todas as decisões da política de ativação do CLR versão 2 herdadas (por exemplo, usando o `useLegacyV2RuntimeActivationPolicy` atributo no [ \< elemento Startup>](../../configure-apps/file-schema/startup/startup-element.md) no arquivo de configuração), esse método não retornará um resultado de erro; em vez disso, o resultado será S_OK, assim como seria se o método tivesse associado com êxito a política de ativação herdada.</span><span class="sxs-lookup"><span data-stu-id="c6050-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6050-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6050-115">Requirements</span></span>  
 <span data-ttu-id="c6050-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6050-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6050-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c6050-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c6050-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c6050-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6050-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6050-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6050-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="c6050-120">See also</span></span>

- [<span data-ttu-id="c6050-121">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="c6050-121">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c6050-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6050-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c6050-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c6050-123">Hosting</span></span>](index.md)
- [<span data-ttu-id="c6050-124">\<Elemento de> de inicialização</span><span class="sxs-lookup"><span data-stu-id="c6050-124">\<startup> Element</span></span>](../../configure-apps/file-schema/startup/startup-element.md)
