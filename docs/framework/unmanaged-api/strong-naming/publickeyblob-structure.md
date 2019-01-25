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
ms.openlocfilehash: 245d9dc6147f4140e823b79c3816b9bc567ad712
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732681"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="e4db9-102">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="e4db9-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="e4db9-103">Representa, em formato binário, a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="e4db9-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4db9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e4db9-104">Syntax</span></span>  
  
```  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="e4db9-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e4db9-105">Members</span></span>  
  
|<span data-ttu-id="e4db9-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e4db9-106">Member</span></span>|<span data-ttu-id="e4db9-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4db9-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="e4db9-108">O identificador para o algoritmo de assinatura (do tipo `ALG_ID`, conforme definido em Wincrypt) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="e4db9-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="e4db9-109">O identificador para o algoritmo de hash (do tipo `ALG_ID`, conforme definido em Wincrypt) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="e4db9-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="e4db9-110">O comprimento da chave em bytes.</span><span class="sxs-lookup"><span data-stu-id="e4db9-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="e4db9-111">Uma matriz de bytes de comprimento variável que contém o valor da chave no formato retornado por CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="e4db9-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4db9-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4db9-112">Remarks</span></span>  
 <span data-ttu-id="e4db9-113">O `PublicKeyBlob` estrutura é usada pelo [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)e outras funções de nome forte para representar a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="e4db9-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4db9-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4db9-114">Requirements</span></span>  
 <span data-ttu-id="e4db9-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4db9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4db9-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e4db9-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e4db9-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e4db9-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4db9-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4db9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4db9-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e4db9-119">See also</span></span>
- [<span data-ttu-id="e4db9-120">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="e4db9-120">StrongNameGetPublicKey Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)
- [<span data-ttu-id="e4db9-121">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="e4db9-121">StrongNameSignatureGeneration Function</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)
- [<span data-ttu-id="e4db9-122">Estruturas de nomenclatura forte</span><span class="sxs-lookup"><span data-stu-id="e4db9-122">Strong Naming Structures</span></span>](https://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)
