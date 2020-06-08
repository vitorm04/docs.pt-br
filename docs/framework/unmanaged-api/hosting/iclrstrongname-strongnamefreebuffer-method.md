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
ms.openlocfilehash: 7aed3e6877bfcd83754d462cdba81ccc229d002f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503998"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="bf23b-102">Método ICLRStrongName::StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="bf23b-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="bf23b-103">Libera a memória que foi alocada com uma chamada anterior para um método de nome forte, como [ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName:: StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md)ou [ICLRStrongName:: StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="bf23b-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf23b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf23b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameFreeBuffer (
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf23b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bf23b-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="bf23b-106">no Um ponteiro para a memória para liberar.</span><span class="sxs-lookup"><span data-stu-id="bf23b-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf23b-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="bf23b-107">Return Value</span></span>  
 <span data-ttu-id="bf23b-108">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="bf23b-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf23b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf23b-109">Requirements</span></span>  
 <span data-ttu-id="bf23b-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf23b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf23b-111">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="bf23b-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bf23b-112">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf23b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf23b-113">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf23b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf23b-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf23b-114">See also</span></span>

- [<span data-ttu-id="bf23b-115">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bf23b-115">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
