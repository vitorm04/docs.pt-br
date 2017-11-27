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
ms.openlocfilehash: 72c2f976a1949ab6107e37f11989be4f17a738ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="a4e72-102">Método ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="a4e72-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="a4e72-103">Libera a memória que foi alocada com uma chamada anterior para um método de nome forte, como [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), ou [ Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="a4e72-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4e72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4e72-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4e72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4e72-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="a4e72-106">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="a4e72-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4e72-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a4e72-107">Return Value</span></span>  
 <span data-ttu-id="a4e72-108">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="a4e72-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e72-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4e72-109">Requirements</span></span>  
 <span data-ttu-id="a4e72-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4e72-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e72-111">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a4e72-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a4e72-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a4e72-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4e72-113">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e72-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e72-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4e72-114">See Also</span></span>  
 [<span data-ttu-id="a4e72-115">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a4e72-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
