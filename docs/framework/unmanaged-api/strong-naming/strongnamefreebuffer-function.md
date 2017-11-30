---
title: "Função StrongNameFreeBuffer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameFreeBuffer
helpviewer_keywords: StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef48c79cc7dc0fb7d881e0cced29741431044551
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamefreebuffer-function"></a><span data-ttu-id="72561-102">Função StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="72561-102">StrongNameFreeBuffer Function</span></span>
<span data-ttu-id="72561-103">Libera a memória que foi alocada com uma chamada anterior a uma função de nome forte, como [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), ou [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span><span class="sxs-lookup"><span data-stu-id="72561-103">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).</span></span>  
  
 <span data-ttu-id="72561-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="72561-104">This function has been deprecated.</span></span> <span data-ttu-id="72561-105">Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72561-105">Use the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72561-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72561-106">Syntax</span></span>  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72561-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72561-107">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="72561-108">[in] Um ponteiro para liberar a memória.</span><span class="sxs-lookup"><span data-stu-id="72561-108">[in] A pointer to the memory to free.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72561-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72561-109">Requirements</span></span>  
 <span data-ttu-id="72561-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72561-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72561-111">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="72561-111">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="72561-112">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="72561-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72561-113">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72561-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72561-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72561-114">See Also</span></span>  
 [<span data-ttu-id="72561-115">Método StrongNameFreeBuffer</span><span class="sxs-lookup"><span data-stu-id="72561-115">StrongNameFreeBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [<span data-ttu-id="72561-116">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="72561-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
