---
title: Função StrongNameFreeBuffer
ms.date: 03/30/2017
api_name:
- StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f308f6c1f977fad8fa102f30756f0e43c779cc8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472051"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="c6086-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="c6086-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="c6086-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="c6086-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="c6086-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c6086-104">This function has been deprecated.</span></span> <span data-ttu-id="c6086-105">Use o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c6086-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6086-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6086-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6086-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6086-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c6086-108">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="c6086-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6086-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6086-109">Requirements</span></span>  
 <span data-ttu-id="c6086-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6086-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6086-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c6086-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c6086-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c6086-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6086-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6086-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6086-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6086-114">See also</span></span>
- [<span data-ttu-id="c6086-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="c6086-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="c6086-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c6086-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
