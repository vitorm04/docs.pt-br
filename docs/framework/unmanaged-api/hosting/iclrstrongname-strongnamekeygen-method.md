---
title: "Método ICLRStrongName::StrongNameKeyGen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b434783d7537c5f6a3127183f66d4b0b3f77534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="ecc5f-102">Método ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="ecc5f-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="ecc5f-103">Cria um novo par de chaves pública/privada para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc5f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecc5f-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecc5f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecc5f-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ecc5f-106">[in] O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-106">[in] The requested key container name.</span></span> <span data-ttu-id="ecc5f-107">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou null para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ecc5f-108">[in] Um valor que especifica se deve deixar a chave registrada.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="ecc5f-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ecc5f-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="ecc5f-110">0x00000000 - usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporária.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="ecc5f-111">0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="ecc5f-112">[out] O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="ecc5f-113">[out] O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecc5f-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ecc5f-114">Return Value</span></span>  
 <span data-ttu-id="ecc5f-115">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="ecc5f-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecc5f-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ecc5f-116">Remarks</span></span>  
 <span data-ttu-id="ecc5f-117">O [Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) método cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="ecc5f-118">Após a chave de recuperação, você deve chamar o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="ecc5f-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc5f-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ecc5f-119">Requirements</span></span>  
 <span data-ttu-id="ecc5f-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc5f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc5f-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ecc5f-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ecc5f-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="ecc5f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecc5f-123">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc5f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc5f-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecc5f-124">See Also</span></span>  
 [<span data-ttu-id="ecc5f-125">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="ecc5f-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="ecc5f-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ecc5f-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
