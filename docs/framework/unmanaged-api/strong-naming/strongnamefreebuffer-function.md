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
ms.openlocfilehash: 9bfc6491a1d18c81a44a7d9c5084f744c9b76281
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040905"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="c1b6f-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="c1b6f-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="c1b6f-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="c1b6f-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="c1b6f-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-104">This function has been deprecated.</span></span> <span data-ttu-id="c1b6f-105">Use o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b6f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1b6f-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1b6f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1b6f-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c1b6f-108">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="c1b6f-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b6f-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1b6f-109">Requirements</span></span>  
 <span data-ttu-id="c1b6f-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b6f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b6f-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c1b6f-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c1b6f-112">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c1b6f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b6f-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1b6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b6f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1b6f-114">See also</span></span>

- [<span data-ttu-id="c1b6f-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="c1b6f-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)
- [<span data-ttu-id="c1b6f-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c1b6f-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
