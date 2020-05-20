---
title: Interface ICLRMetaHostPolicy
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy
helpviewer_keywords:
- ICLRMetaHostPolicy interface [.NET Framework hosting]
ms.assetid: 1bdeccb6-0698-4c97-ad69-eae2b69e59f1
topic_type:
- apiref
ms.openlocfilehash: 79b62a5e2aad9cfcd14ba40c1abf0342bfe57a4b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703535"
---
# <a name="iclrmetahostpolicy-interface"></a><span data-ttu-id="a7ce7-102">Interface ICLRMetaHostPolicy</span><span class="sxs-lookup"><span data-stu-id="a7ce7-102">ICLRMetaHostPolicy Interface</span></span>
<span data-ttu-id="a7ce7-103">Fornece o método [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) , que retorna um ponteiro para uma interface Common Language Runtime (CLR) com base em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-103">Provides the [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) method, which returns a pointer to a common language runtime (CLR) interface based on a policy criteria, managed assembly, version and configuration file.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a7ce7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a7ce7-104">Methods</span></span>  
  
|<span data-ttu-id="a7ce7-105">Método</span><span class="sxs-lookup"><span data-stu-id="a7ce7-105">Method</span></span>|<span data-ttu-id="a7ce7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7ce7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a7ce7-107">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="a7ce7-107">GetRequestedRuntime Method</span></span>](iclrmetahostpolicy-getrequestedruntime-method.md)|<span data-ttu-id="a7ce7-108">Fornece uma interface CLR preferida com base em critérios de política, assembly gerenciado, versão e arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-108">Provides a preferred CLR interface based on a policy criteria, managed assembly, version, and configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ce7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a7ce7-109">Remarks</span></span>  
 <span data-ttu-id="a7ce7-110">Você pode obter uma referência a essa interface chamando a função [CLRCreateInstance](clrcreateinstance-function.md) , conforme mostrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="a7ce7-110">You can get a reference to this interface by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as shown in the following code:</span></span>  
  
```cpp  
ICLRMetaHostPolicy *pMetaHostPolicy = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHostPolicy,  
                   IID_ICLRMetaHostPolicy, (LPVOID*)&pMetaHostPolicy);  
```  
  
> [!NOTE]
> <span data-ttu-id="a7ce7-111">Essa interface, na verdade, não carrega nem ativa o CLR, mas simplesmente retorna a versão do CLR preferida com base nas versões disponíveis que estão instaladas ou carregadas.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-111">This interface does not actually load or activate the CLR, but simply returns the preferred CLR version based on the available versions that are installed or loaded.</span></span>  
  
 <span data-ttu-id="a7ce7-112">A API de hospedagem do .NET Framework 4 consolida políticas para que os hosts com necessidades específicas possam usar a funcionalidade básica sem incorrer em penalidades involuntárias.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-112">The .NET Framework 4 hosting API consolidates policies so that hosts with specific needs may use basic functionality without incurring unintended penalties.</span></span> <span data-ttu-id="a7ce7-113">Por exemplo, muitas das exportações de MSCorEE. dll serão vinculadas a um CLR específico, embora um método possa não exigi-la logicamente.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-113">For example, many of the MSCorEE.dll exports will bind to a specific CLR, although a method might not logically require it.</span></span> <span data-ttu-id="a7ce7-114">A enumeração de [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) fornece políticas de associação que são comuns à maioria dos hosts.</span><span class="sxs-lookup"><span data-stu-id="a7ce7-114">The [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration provides binding policies that are common to the majority of hosts.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ce7-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7ce7-115">Requirements</span></span>  
 <span data-ttu-id="a7ce7-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7ce7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ce7-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a7ce7-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a7ce7-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a7ce7-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7ce7-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ce7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ce7-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="a7ce7-120">See also</span></span>

- [<span data-ttu-id="a7ce7-121">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="a7ce7-121">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="a7ce7-122">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a7ce7-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="a7ce7-123">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a7ce7-123">Hosting</span></span>](index.md)
