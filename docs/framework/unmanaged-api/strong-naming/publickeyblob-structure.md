---
title: Estrutura PublicKeyBlob
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a361e04b6f8f39ec0083471d8cb47d5a29376c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214813"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="ff2e5-102">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="ff2e5-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="ff2e5-103">Representa, em formato binário, a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff2e5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff2e5-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="ff2e5-105">Membros</span><span class="sxs-lookup"><span data-stu-id="ff2e5-105">Members</span></span>  
  
|<span data-ttu-id="ff2e5-106">Membro</span><span class="sxs-lookup"><span data-stu-id="ff2e5-106">Member</span></span>|<span data-ttu-id="ff2e5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff2e5-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="ff2e5-108">O identificador para o algoritmo de assinatura (do tipo `ALG_ID`, conforme definido em Wincrypt) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="ff2e5-109">O identificador para o algoritmo de hash (do tipo `ALG_ID`, conforme definido em Wincrypt) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="ff2e5-110">O comprimento da chave em bytes.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="ff2e5-111">Uma matriz de bytes de comprimento variável que contém o valor da chave no formato retornado por CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff2e5-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff2e5-112">Remarks</span></span>  
 <span data-ttu-id="ff2e5-113">O `PublicKeyBlob` estrutura é usada pelo [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)e outras funções de nome forte para representar a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="ff2e5-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2e5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff2e5-114">Requirements</span></span>  
 <span data-ttu-id="ff2e5-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff2e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2e5-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ff2e5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ff2e5-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ff2e5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ff2e5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2e5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff2e5-119">See also</span></span>

- [<span data-ttu-id="ff2e5-120">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="ff2e5-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="ff2e5-121">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="ff2e5-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
