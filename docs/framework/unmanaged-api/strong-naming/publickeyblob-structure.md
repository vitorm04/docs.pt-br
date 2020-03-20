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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176949"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="b5aa7-102">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="b5aa7-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="b5aa7-103">Representa, em formato binário, a chave pública de um par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5aa7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5aa7-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="b5aa7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b5aa7-105">Members</span></span>  
  
|<span data-ttu-id="b5aa7-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b5aa7-106">Member</span></span>|<span data-ttu-id="b5aa7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5aa7-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="b5aa7-108">O identificador para o algoritmo `ALG_ID`de assinatura (do tipo, conforme definido no WinCrypt.h) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="b5aa7-109">O identificador para o algoritmo `ALG_ID`hash (do tipo , conforme definido no WinCrypt.h) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="b5aa7-110">O comprimento da chave em bytes.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="b5aa7-111">Uma matriz de byte de comprimento variável que contém o valor-chave no formato retornado pelo CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5aa7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5aa7-112">Remarks</span></span>  
 <span data-ttu-id="b5aa7-113">A `PublicKeyBlob` estrutura é usada por [StrongNameGetPublicKey,](strongnamegetpublickey-function.md) [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)e outras funções de nome forte para representar a chave pública de um par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="b5aa7-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5aa7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5aa7-114">Requirements</span></span>  
 <span data-ttu-id="b5aa7-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5aa7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5aa7-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b5aa7-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b5aa7-117">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b5aa7-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5aa7-118">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5aa7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5aa7-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5aa7-119">See also</span></span>

- [<span data-ttu-id="b5aa7-120">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="b5aa7-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="b5aa7-121">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="b5aa7-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
