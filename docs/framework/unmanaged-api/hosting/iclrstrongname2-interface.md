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
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092238"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="1677c-102">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="1677c-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="1677c-103">Fornece a capacidade de criar nomes fortes usando o grupo SHA-2 de algoritmos de hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="1677c-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1677c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1677c-104">Methods</span></span>  
  
|<span data-ttu-id="1677c-105">Método</span><span class="sxs-lookup"><span data-stu-id="1677c-105">Method</span></span>|<span data-ttu-id="1677c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1677c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1677c-107">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="1677c-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="1677c-108">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="1677c-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="1677c-109">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="1677c-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="1677c-110">Verifica a assinatura de um assembly com nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="1677c-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1677c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1677c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1677c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1677c-112">Requirements</span></span>  
 <span data-ttu-id="1677c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1677c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1677c-114">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1677c-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1677c-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1677c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1677c-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1677c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
