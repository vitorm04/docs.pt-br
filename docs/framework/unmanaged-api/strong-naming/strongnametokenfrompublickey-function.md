---
title: Função StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175051"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="69011-102">Função StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="69011-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="69011-103">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="69011-103">Gets a token representing a public key.</span></span> <span data-ttu-id="69011-104">Um nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="69011-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="69011-105">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="69011-105">This function has been deprecated.</span></span> <span data-ttu-id="69011-106">Use o método [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)</span><span class="sxs-lookup"><span data-stu-id="69011-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69011-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69011-107">Syntax</span></span>  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69011-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="69011-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="69011-109">[em] Uma estrutura do tipo [PublicKeyBlob](publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="69011-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="69011-110">[em] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="69011-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="69011-111">[fora] O token de nome forte `pbPublicKeyBlob`correspondente à chave passou em .</span><span class="sxs-lookup"><span data-stu-id="69011-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="69011-112">O tempo de execução do idioma comum aloca a memória na qual o token retorna.</span><span class="sxs-lookup"><span data-stu-id="69011-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="69011-113">O chamador deve liberar essa memória usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="69011-113">The caller must free this memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="69011-114">[fora] O tamanho, em bytes, do nome forte devolvido token.</span><span class="sxs-lookup"><span data-stu-id="69011-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69011-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="69011-115">Return Value</span></span>  
 <span data-ttu-id="69011-116">`true`em conclusão bem sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="69011-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69011-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="69011-117">Remarks</span></span>  
 <span data-ttu-id="69011-118">Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações-chave em metadados.</span><span class="sxs-lookup"><span data-stu-id="69011-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="69011-119">Especificamente, tokens de nome fortes são usados em referências de montagem para se referir ao conjunto dependente.</span><span class="sxs-lookup"><span data-stu-id="69011-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="69011-120">Se `StrongNameTokenFromPublicKey` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="69011-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69011-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69011-121">Requirements</span></span>  
 <span data-ttu-id="69011-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69011-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69011-123">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="69011-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="69011-124">**Biblioteca:** Incluído como um recurso em mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="69011-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="69011-125">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69011-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69011-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="69011-126">See also</span></span>

- [<span data-ttu-id="69011-127">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="69011-127">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="69011-128">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="69011-128">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="69011-129">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="69011-129">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
