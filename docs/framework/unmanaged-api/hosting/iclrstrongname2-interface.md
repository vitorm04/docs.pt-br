---
title: Interface ICLRStrongName2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d4e1274f675ae9289faa6c530d34cd61d033aa07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="9af73-102">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="9af73-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="9af73-103">Fornece a capacidade de criar nomes de alta segurança usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="9af73-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9af73-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9af73-104">Methods</span></span>  
  
|<span data-ttu-id="9af73-105">Método</span><span class="sxs-lookup"><span data-stu-id="9af73-105">Method</span></span>|<span data-ttu-id="9af73-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9af73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9af73-107">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="9af73-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="9af73-108">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="9af73-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="9af73-109">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="9af73-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="9af73-110">Verifica a assinatura de um assembly de nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="9af73-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9af73-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="9af73-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9af73-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9af73-112">Requirements</span></span>  
 <span data-ttu-id="9af73-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af73-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9af73-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9af73-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9af73-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9af73-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9af73-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9af73-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
