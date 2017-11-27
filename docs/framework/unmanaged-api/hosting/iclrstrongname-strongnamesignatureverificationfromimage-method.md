---
title: "Método ICLRStrongName::StrongNameSignatureVerificationFromImage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f312e1eade6de57df9660a349570398d9cd912b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="7acce-102">Método ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="7acce-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="7acce-103">Verifica se um assembly que já foi mapeado para a memória é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="7acce-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7acce-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7acce-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7acce-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7acce-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="7acce-106">[in] O endereço virtual relativo do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="7acce-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7acce-107">[in] O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="7acce-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="7acce-108">[in] Sinalizadores que influenciam o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="7acce-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="7acce-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7acce-109">The following values are supported:</span></span>  
  
-   <span data-ttu-id="7acce-110">`SN_INFLAG_FORCE_VER`(0x00000001) - força a verificação mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="7acce-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   <span data-ttu-id="7acce-111">`SN_INFLAG_INSTALL`(0x00000002) - Especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="7acce-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
-   <span data-ttu-id="7acce-112">`SN_INFLAG_ADMIN_ACCESS`(0x00000004) - Especifica que o cache permite acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="7acce-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   <span data-ttu-id="7acce-113">`SN_INFLAG_USER_ACCESS`(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="7acce-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   <span data-ttu-id="7acce-114">`SN_INFLAG_ALL_ACCESS`(0x00000010) - Especifica que o cache não fornecem nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="7acce-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   <span data-ttu-id="7acce-115">`SN_INFLAG_RUNTIME`(0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="7acce-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="7acce-116">[out] Um sinalizador para obter informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="7acce-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="7acce-117">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="7acce-117">The following value is supported:</span></span>  
  
-   <span data-ttu-id="7acce-118">`SN_OUTFLAG_WAS_VERIFIED`(0x00000001) - Este valor é definido como `false` para especificar se a verificação foi bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="7acce-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7acce-119">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7acce-119">Return Value</span></span>  
 <span data-ttu-id="7acce-120">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="7acce-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7acce-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7acce-121">Requirements</span></span>  
 <span data-ttu-id="7acce-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7acce-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7acce-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7acce-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7acce-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7acce-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7acce-125">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7acce-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7acce-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7acce-126">See Also</span></span>  
 [<span data-ttu-id="7acce-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7acce-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
