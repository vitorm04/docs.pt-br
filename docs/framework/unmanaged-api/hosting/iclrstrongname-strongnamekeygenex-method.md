---
title: "Método ICLRStrongName::StrongNameKeyGenEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyGenEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 581f486a2def90f44c0fb3f1bcf9d3bbcc1fc317
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="bc248-102">Método ICLRStrongName::StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="bc248-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="bc248-103">Gera um novo par de chaves pública/privada com o tamanho de chave especificado para o uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="bc248-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc248-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bc248-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc248-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bc248-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="bc248-106">[in] O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="bc248-106">[in] The requested key container name.</span></span> <span data-ttu-id="bc248-107">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou null para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="bc248-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bc248-108">[in] Um valor que especifica se deve deixar a chave registrada.</span><span class="sxs-lookup"><span data-stu-id="bc248-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="bc248-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bc248-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="bc248-110">0x00000000 - usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporária.</span><span class="sxs-lookup"><span data-stu-id="bc248-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="bc248-111">0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="bc248-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="bc248-112">[in] O tamanho solicitado da chave em bits.</span><span class="sxs-lookup"><span data-stu-id="bc248-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="bc248-113">[out] O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="bc248-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="bc248-114">[out] O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bc248-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc248-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bc248-115">Return Value</span></span>  
 <span data-ttu-id="bc248-116">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="bc248-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc248-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="bc248-117">Remarks</span></span>  
 <span data-ttu-id="bc248-118">As versões do .NET Framework 1.0 e 1.1 exigem um `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2.0 adiciona suporte para chaves de 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="bc248-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="bc248-119">Após a chave de recuperação, você deve chamar o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="bc248-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc248-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bc248-120">Requirements</span></span>  
 <span data-ttu-id="bc248-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc248-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc248-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bc248-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bc248-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="bc248-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc248-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc248-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc248-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc248-125">See Also</span></span>  
 [<span data-ttu-id="bc248-126">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="bc248-126">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="bc248-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bc248-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
