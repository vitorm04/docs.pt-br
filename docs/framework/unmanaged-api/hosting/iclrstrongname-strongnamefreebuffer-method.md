---
title: "Método ICLRStrongName::StrongNameFreeBuffer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameFreeBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 378847ae8bfd1640401c51f75258affbd100cb22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="d73d3-102">Método ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="d73d3-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="d73d3-103">Libera a memória que foi alocada com uma chamada anterior para um método de nome forte, como [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), ou [ Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="d73d3-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d73d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d73d3-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d73d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d73d3-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="d73d3-106">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="d73d3-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d73d3-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d73d3-107">Return Value</span></span>  
 <span data-ttu-id="d73d3-108">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="d73d3-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73d3-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d73d3-109">Requirements</span></span>  
 <span data-ttu-id="d73d3-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d73d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73d3-111">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d73d3-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d73d3-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d73d3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d73d3-113">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73d3-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d73d3-114">See Also</span></span>  
 [<span data-ttu-id="d73d3-115">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d73d3-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
