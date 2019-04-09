---
title: Método ICLRStrongName::StrongNameGetBlobFromImage
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fa83f55a03ebfff9ae88217b01c86272bf0de93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178965"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="1740c-102">Método ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="1740c-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="1740c-103">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="1740c-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1740c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1740c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1740c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1740c-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="1740c-106">[in] O endereço de memória do manifesto do assembly mapeados.</span><span class="sxs-lookup"><span data-stu-id="1740c-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="1740c-107">[in] O tamanho, em bytes, da imagem no `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="1740c-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="1740c-108">[in] Um buffer que conterá a representação binária da imagem.</span><span class="sxs-lookup"><span data-stu-id="1740c-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="1740c-109">[no, out] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="1740c-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="1740c-110">Após o retorno, o tamanho real, em bytes, do `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="1740c-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1740c-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1740c-111">Return Value</span></span>  
 `S_OK` <span data-ttu-id="1740c-112">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="1740c-112">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1740c-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1740c-113">Requirements</span></span>  
 <span data-ttu-id="1740c-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1740c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1740c-115">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1740c-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1740c-116">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="1740c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="1740c-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1740c-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1740c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1740c-118">See also</span></span>

- [<span data-ttu-id="1740c-119">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="1740c-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="1740c-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="1740c-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
