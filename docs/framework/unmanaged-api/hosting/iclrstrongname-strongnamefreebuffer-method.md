---
title: Método ICLRStrongName::StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
ms.openlocfilehash: e3d0c4791f6d487522ef4bb0ba31ccb6042589c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135108"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="c3ff1-102">Método ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="c3ff1-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="c3ff1-103">Libera a memória que foi alocada com uma chamada anterior para um método de nome forte, como [ICLRStrongName:: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName:: StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)ou [ICLRStrongName:: StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3ff1-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3ff1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3ff1-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3ff1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c3ff1-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c3ff1-106">no Um ponteiro para a memória para liberar.</span><span class="sxs-lookup"><span data-stu-id="c3ff1-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3ff1-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c3ff1-107">Return Value</span></span>  
 <span data-ttu-id="c3ff1-108">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="c3ff1-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3ff1-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3ff1-109">Requirements</span></span>  
 <span data-ttu-id="c3ff1-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3ff1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3ff1-111">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c3ff1-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c3ff1-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c3ff1-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3ff1-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3ff1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3ff1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3ff1-114">See also</span></span>

- [<span data-ttu-id="c3ff1-115">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c3ff1-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
