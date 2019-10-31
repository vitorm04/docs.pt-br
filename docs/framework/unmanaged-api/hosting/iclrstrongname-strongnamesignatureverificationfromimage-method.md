---
title: Método ICLRStrongName::StrongNameSignatureVerificationFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: adb3b4e33edafe6d25c8259e316a9b62e339f896
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092676"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="b00a8-102">Método ICLRStrongName::StrongNameSignatureVerificationFromImage</span><span class="sxs-lookup"><span data-stu-id="b00a8-102">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>
<span data-ttu-id="b00a8-103">Verifica se um assembly, que já foi mapeado para a memória, é válido para a chave pública associada.</span><span class="sxs-lookup"><span data-stu-id="b00a8-103">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b00a8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b00a8-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b00a8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b00a8-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="b00a8-106">no O endereço virtual relativo do manifesto do assembly mapeado.</span><span class="sxs-lookup"><span data-stu-id="b00a8-106">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b00a8-107">no O tamanho, em bytes, da imagem mapeada.</span><span class="sxs-lookup"><span data-stu-id="b00a8-107">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="b00a8-108">no Sinalizadores que influenciam o comportamento da verificação.</span><span class="sxs-lookup"><span data-stu-id="b00a8-108">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="b00a8-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b00a8-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="b00a8-110">`SN_INFLAG_FORCE_VER` (0x00000001) – força a verificação mesmo que seja necessário substituir as configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="b00a8-110">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="b00a8-111">`SN_INFLAG_INSTALL` (0x00000002) – especifica que esta é a primeira verificação executada nesta imagem.</span><span class="sxs-lookup"><span data-stu-id="b00a8-111">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="b00a8-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) – especifica que o cache permitirá acesso somente aos usuários que têm privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="b00a8-112">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="b00a8-113">`SN_INFLAG_USER_ACCESS` (0x00000008) – especifica que o assembly será acessível somente para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="b00a8-113">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="b00a8-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) – especifica que o cache não fornecerá nenhuma garantia de restrição de acesso.</span><span class="sxs-lookup"><span data-stu-id="b00a8-114">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="b00a8-115">`SN_INFLAG_RUNTIME` (0x80000000) – reservado para depuração interna.</span><span class="sxs-lookup"><span data-stu-id="b00a8-115">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="b00a8-116">fora Um sinalizador para informações de saída adicionais.</span><span class="sxs-lookup"><span data-stu-id="b00a8-116">[out] A flag for additional output information.</span></span> <span data-ttu-id="b00a8-117">Há suporte para o seguinte valor:</span><span class="sxs-lookup"><span data-stu-id="b00a8-117">The following value is supported:</span></span>  
  
- <span data-ttu-id="b00a8-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-esse valor é definido como `false` para especificar que a verificação foi bem-sucedida devido às configurações do registro.</span><span class="sxs-lookup"><span data-stu-id="b00a8-118">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b00a8-119">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b00a8-119">Return Value</span></span>  
 <span data-ttu-id="b00a8-120">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="b00a8-120">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b00a8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b00a8-121">Requirements</span></span>  
 <span data-ttu-id="b00a8-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b00a8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b00a8-123">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="b00a8-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b00a8-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b00a8-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b00a8-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b00a8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00a8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b00a8-126">See also</span></span>

- [<span data-ttu-id="b00a8-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b00a8-127">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
