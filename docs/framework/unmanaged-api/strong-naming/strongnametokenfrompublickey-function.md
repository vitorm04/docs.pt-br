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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb8ff76da288975ef291d226bb1f205e73a64252
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460282"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="ab411-102">Função StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab411-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="ab411-103">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="ab411-103">Gets a token representing a public key.</span></span> <span data-ttu-id="ab411-104">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="ab411-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="ab411-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="ab411-105">This function has been deprecated.</span></span> <span data-ttu-id="ab411-106">Use o [: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ab411-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab411-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab411-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab411-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab411-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="ab411-109">[in] Uma estrutura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ab411-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="ab411-110">[in] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ab411-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="ab411-111">[out] O token de nome forte correspondente à chave passada `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ab411-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="ab411-112">O common language runtime aloca a memória no qual retornar o token.</span><span class="sxs-lookup"><span data-stu-id="ab411-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="ab411-113">O chamador deve liberar esta memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="ab411-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="ab411-114">[out] O tamanho, em bytes, do token retornado de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ab411-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab411-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ab411-115">Return Value</span></span>  
 <span data-ttu-id="ab411-116">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab411-116">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab411-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab411-117">Remarks</span></span>  
 <span data-ttu-id="ab411-118">Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações importantes nos metadados.</span><span class="sxs-lookup"><span data-stu-id="ab411-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="ab411-119">Especificamente, os tokens de nome forte são usados em referências de assembly para referenciar o assembly dependente.</span><span class="sxs-lookup"><span data-stu-id="ab411-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="ab411-120">Se o `StrongNameTokenFromPublicKey` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="ab411-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab411-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab411-121">Requirements</span></span>  
 <span data-ttu-id="ab411-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab411-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab411-123">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ab411-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ab411-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ab411-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="ab411-125">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab411-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab411-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab411-126">See Also</span></span>  
 [<span data-ttu-id="ab411-127">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab411-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="ab411-128">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab411-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="ab411-129">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="ab411-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
