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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140610"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="f6db3-102">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="f6db3-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="f6db3-103">Representa, em formato binário, a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="f6db3-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6db3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f6db3-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="f6db3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f6db3-105">Members</span></span>  
  
|<span data-ttu-id="f6db3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f6db3-106">Member</span></span>|<span data-ttu-id="f6db3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6db3-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="f6db3-108">O identificador do algoritmo de assinatura (do tipo `ALG_ID`, conforme definido em WinCrypt. h) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="f6db3-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="f6db3-109">O identificador do algoritmo de hash (do tipo `ALG_ID`, conforme definido em WinCrypt. h) da chave pública.</span><span class="sxs-lookup"><span data-stu-id="f6db3-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="f6db3-110">O comprimento da chave em bytes.</span><span class="sxs-lookup"><span data-stu-id="f6db3-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="f6db3-111">Uma matriz de bytes de comprimento variável que contém o valor da chave no formato retornado pela CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="f6db3-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6db3-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f6db3-112">Remarks</span></span>  
 <span data-ttu-id="f6db3-113">A estrutura de `PublicKeyBlob` é usada por [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)e outras funções de nome forte para representar a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="f6db3-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6db3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f6db3-114">Requirements</span></span>  
 <span data-ttu-id="f6db3-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6db3-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6db3-116">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="f6db3-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f6db3-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f6db3-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6db3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6db3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6db3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f6db3-119">See also</span></span>

- [<span data-ttu-id="f6db3-120">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="f6db3-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="f6db3-121">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="f6db3-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
