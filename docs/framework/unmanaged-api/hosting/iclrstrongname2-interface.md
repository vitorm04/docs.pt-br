---
title: Interface ICLRStrongName2
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf9e3d2df8f507e118b393007c3958358a830cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="2b4d0-102">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="2b4d0-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="2b4d0-103">Fornece a capacidade de criar nomes de alta segurança usando o grupo de SHA-2 de algoritmos de Hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="2b4d0-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b4d0-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2b4d0-104">Methods</span></span>  
  
|<span data-ttu-id="2b4d0-105">Método</span><span class="sxs-lookup"><span data-stu-id="2b4d0-105">Method</span></span>|<span data-ttu-id="2b4d0-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b4d0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b4d0-107">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="2b4d0-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="2b4d0-108">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="2b4d0-109">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="2b4d0-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="2b4d0-110">Verifica a assinatura de um assembly de nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="2b4d0-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b4d0-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b4d0-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b4d0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b4d0-112">Requirements</span></span>  
 <span data-ttu-id="2b4d0-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4d0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b4d0-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2b4d0-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2b4d0-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2b4d0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b4d0-116">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
