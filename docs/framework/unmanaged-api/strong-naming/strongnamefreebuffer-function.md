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
ms.openlocfilehash: 1a129608370cd72967e0c441eff12b4aca7e638c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455082"
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="fb4f5-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="fb4f5-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="fb4f5-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="fb4f5-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="fb4f5-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="fb4f5-104">This function has been deprecated.</span></span> <span data-ttu-id="fb4f5-105">Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="fb4f5-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb4f5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb4f5-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb4f5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb4f5-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="fb4f5-108">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="fb4f5-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb4f5-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb4f5-109">Requirements</span></span>  
 <span data-ttu-id="fb4f5-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb4f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb4f5-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="fb4f5-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fb4f5-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="fb4f5-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb4f5-113">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb4f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4f5-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb4f5-114">See Also</span></span>  
 [<span data-ttu-id="fb4f5-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="fb4f5-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="fb4f5-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fb4f5-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
