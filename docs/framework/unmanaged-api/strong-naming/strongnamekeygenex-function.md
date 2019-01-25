---
title: Função StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77ede995b08aba0822e9d86607e0d1e37bd6f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557325"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="57711-102">Função StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="57711-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="57711-103">Gera um novo par de chaves pública/privada com o tamanho da chave especificado, para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="57711-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="57711-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="57711-104">This function has been deprecated.</span></span> <span data-ttu-id="57711-105">Use o [iclrstrongname:: Strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="57711-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57711-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57711-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57711-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57711-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="57711-108">[in] O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="57711-108">[in] The requested key container name.</span></span> <span data-ttu-id="57711-109">`wszKeyContainer` deve ser uma cadeia de caracteres vazio ou nulo para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="57711-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="57711-110">[in] Especifica se é necessário deixar a chave registrada.</span><span class="sxs-lookup"><span data-stu-id="57711-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="57711-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="57711-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="57711-112">0x00000000 - usado quando `wszKeyContainer` é nula para gerar um nome de contêiner de chave temporária.</span><span class="sxs-lookup"><span data-stu-id="57711-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="57711-113">0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="57711-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="57711-114">[in] O tamanho solicitado da chave, em bits.</span><span class="sxs-lookup"><span data-stu-id="57711-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="57711-115">[out] O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="57711-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="57711-116">[out] O tamanho, em bytes, do `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="57711-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57711-117">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="57711-117">Return Value</span></span>  
 <span data-ttu-id="57711-118">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="57711-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57711-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="57711-119">Remarks</span></span>  
 <span data-ttu-id="57711-120">As versões do .NET Framework 1.0 e 1.1 requerem um `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2.0 adiciona suporte para chaves de 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="57711-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="57711-121">Após a chave de recuperação, você deve chamar o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="57711-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="57711-122">Se o `StrongNameKeyGenEx` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="57711-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57711-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57711-123">Requirements</span></span>  
 <span data-ttu-id="57711-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57711-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57711-125">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="57711-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="57711-126">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="57711-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57711-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57711-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57711-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57711-128">See also</span></span>
- [<span data-ttu-id="57711-129">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="57711-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="57711-130">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="57711-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="57711-131">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="57711-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
