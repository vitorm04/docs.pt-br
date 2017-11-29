---
title: Interface ICLRStrongName2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9e9a88f1064c888d60e363be569d06458299143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="03489-102">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="03489-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="03489-103">Fornece a capacidade de criar nomes de alta segurança usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="03489-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03489-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="03489-104">Methods</span></span>  
  
|<span data-ttu-id="03489-105">Método</span><span class="sxs-lookup"><span data-stu-id="03489-105">Method</span></span>|<span data-ttu-id="03489-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="03489-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03489-107">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="03489-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="03489-108">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="03489-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="03489-109">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="03489-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="03489-110">Verifica a assinatura de um assembly de nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="03489-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03489-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="03489-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03489-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03489-112">Requirements</span></span>  
 <span data-ttu-id="03489-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03489-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03489-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="03489-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="03489-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="03489-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03489-116">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03489-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
