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
ms.openlocfilehash: 9715369f4cf1b2a7078be14a2fc597f735ab6fd3
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763157"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="1428c-102">Interface ICLRStrongName2</span><span class="sxs-lookup"><span data-stu-id="1428c-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="1428c-103">Fornece a capacidade de criar nomes fortes usando o grupo SHA-2 de algoritmos de hash seguro (SHA-256, SHA-384 e SHA-512).</span><span class="sxs-lookup"><span data-stu-id="1428c-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1428c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="1428c-104">Methods</span></span>  
  
|<span data-ttu-id="1428c-105">Método</span><span class="sxs-lookup"><span data-stu-id="1428c-105">Method</span></span>|<span data-ttu-id="1428c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="1428c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1428c-107">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="1428c-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="1428c-108">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="1428c-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="1428c-109">Método StrongNameSignatureVerificationEx2</span><span class="sxs-lookup"><span data-stu-id="1428c-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="1428c-110">Verifica a assinatura de um assembly com nome forte e fornece um mapeamento da chave ECMA para uma chave real.</span><span class="sxs-lookup"><span data-stu-id="1428c-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1428c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="1428c-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1428c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1428c-112">Requirements</span></span>  
 <span data-ttu-id="1428c-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1428c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1428c-114">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1428c-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1428c-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1428c-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1428c-116">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1428c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
