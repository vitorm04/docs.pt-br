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
ms.openlocfilehash: fbfd3ae32f4d3033894fdaf6b1bcc880c324e928
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219792"
---
# <a name="strongnametokenfrompublickey-function"></a><span data-ttu-id="a472f-102">Função StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="a472f-102">StrongNameTokenFromPublicKey Function</span></span>
<span data-ttu-id="a472f-103">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="a472f-103">Gets a token representing a public key.</span></span> <span data-ttu-id="a472f-104">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="a472f-104">A strong name token is the shortened form of a public key.</span></span>  
  
 <span data-ttu-id="a472f-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="a472f-105">This function has been deprecated.</span></span> <span data-ttu-id="a472f-106">Use o [iclrstrongname:: Strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a472f-106">Use the [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a472f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a472f-107">Syntax</span></span>  
  
```  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a472f-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a472f-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="a472f-109">[in] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="a472f-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="a472f-110">[in] O tamanho, em bytes, do `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a472f-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="a472f-111">[out] O token de nome forte correspondente à chave passada `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a472f-111">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="a472f-112">O common language runtime aloca a memória no qual retornar o token.</span><span class="sxs-lookup"><span data-stu-id="a472f-112">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="a472f-113">O chamador deve liberar essa memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="a472f-113">The caller must free this memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="a472f-114">[out] O tamanho, em bytes, do token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="a472f-114">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a472f-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a472f-115">Return Value</span></span>  
 `true` <span data-ttu-id="a472f-116">Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="a472f-116">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a472f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a472f-117">Remarks</span></span>  
 <span data-ttu-id="a472f-118">Um token de nome forte é a forma abreviada de uma chave pública usada para economizar espaço ao armazenar informações de chave nos metadados.</span><span class="sxs-lookup"><span data-stu-id="a472f-118">A strong name token is the shortened form of a public key used to save space when storing key information in metadata.</span></span> <span data-ttu-id="a472f-119">Especificamente, os tokens de nome forte são usados nas referências de assembly para fazer referência ao assembly dependente.</span><span class="sxs-lookup"><span data-stu-id="a472f-119">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
 <span data-ttu-id="a472f-120">Se o `StrongNameTokenFromPublicKey` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="a472f-120">If the `StrongNameTokenFromPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a472f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a472f-121">Requirements</span></span>  
 <span data-ttu-id="a472f-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a472f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a472f-123">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a472f-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a472f-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="a472f-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 **<span data-ttu-id="a472f-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a472f-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a472f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a472f-126">See also</span></span>

- [<span data-ttu-id="a472f-127">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="a472f-127">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a472f-128">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="a472f-128">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="a472f-129">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="a472f-129">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
