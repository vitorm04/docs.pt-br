---
title: Método ICLRStrongName::StrongNameSignatureVerification
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerification
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerification method [.NET Framework hosting]
- StrongNameSignatureVerification method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 734dc4d1-0a76-4736-b5ac-cb4253b3dd49
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9fb7098c29768821cafad6662b646eb0e08a138
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212837"
---
# <a name="iclrstrongnamestrongnamesignatureverification-method"></a><span data-ttu-id="6e96d-102">Método ICLRStrongName::StrongNameSignatureVerification</span><span class="sxs-lookup"><span data-stu-id="6e96d-102">ICLRStrongName::StrongNameSignatureVerification Method</span></span>
<span data-ttu-id="6e96d-103">Obtém um valor que indica se o manifesto do assembly no caminho fornecido contém uma assinatura de nome forte, que é verificada de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="6e96d-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e96d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e96d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e96d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e96d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6e96d-106">[in] O caminho para o arquivo executável portátil (. dll ou .exe) para o assembly verificar.</span><span class="sxs-lookup"><span data-stu-id="6e96d-106">[in] The path to the portable executable (.dll or .exe) file for the assembly to verify.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="6e96d-107">[in] Sinalizadores para modificar o comportamento de verificação.</span><span class="sxs-lookup"><span data-stu-id="6e96d-107">[in] Flags to modify the verification behavior.</span></span> <span data-ttu-id="6e96d-108">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="6e96d-108">The following values are supported:</span></span>  
  
-   `SN_INFLAG_FORCE_VER` <span data-ttu-id="6e96d-109">(0x00000001) - força a verificação, mesmo se for necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="6e96d-109">(0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
-   `SN_INFLAG_INSTALL` <span data-ttu-id="6e96d-110">(0x00000002) - Especifica que esta é a primeira vez que o manifesto é verificado.</span><span class="sxs-lookup"><span data-stu-id="6e96d-110">(0x00000002) - Specifies that this is the first time the manifest is verified.</span></span>  
  
-   `SN_INFLAG_ADMIN_ACCESS` <span data-ttu-id="6e96d-111">(0x00000004) - Especifica que o cache permitirá o acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="6e96d-111">(0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
-   `SN_INFLAG_USER_ACCESS` <span data-ttu-id="6e96d-112">(0x00000008) - Especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="6e96d-112">(0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
-   `SN_INFLAG_ALL_ACCESS` <span data-ttu-id="6e96d-113">(0x00000010) - Especifica que o cache não será fornecer nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="6e96d-113">(0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
-   `SN_INFLAG_RUNTIME` <span data-ttu-id="6e96d-114">(0x80000000) - reservado para a depuração.</span><span class="sxs-lookup"><span data-stu-id="6e96d-114">(0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="6e96d-115">[out] Sinalizadores que indica se a assinatura de nome forte foi verificada.</span><span class="sxs-lookup"><span data-stu-id="6e96d-115">[out] Flags indicating whether the strong name signature was verified.</span></span> <span data-ttu-id="6e96d-116">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="6e96d-116">The following value is supported:</span></span>  
  
-   `SN_OUTFLAG_WAS_VERIFIED` <span data-ttu-id="6e96d-117">(0x00000001) - esse valor é definido como `false` para especificar que a verificação for bem-sucedida devido a configurações de registro.</span><span class="sxs-lookup"><span data-stu-id="6e96d-117">(0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e96d-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6e96d-118">Return Value</span></span>  
 `S_OK` <span data-ttu-id="6e96d-119">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="6e96d-119">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e96d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6e96d-120">Requirements</span></span>  
 <span data-ttu-id="6e96d-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e96d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e96d-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6e96d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6e96d-123">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6e96d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="6e96d-124">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="6e96d-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e96d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e96d-125">See also</span></span>

- [<span data-ttu-id="6e96d-126">Método StrongNameSignatureVerificationEx</span><span class="sxs-lookup"><span data-stu-id="6e96d-126">StrongNameSignatureVerificationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [<span data-ttu-id="6e96d-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6e96d-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
