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
ms.openlocfilehash: ad3b151165eb233bd3a4a78d8f4d612a696b7e93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135103"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a><span data-ttu-id="d77b5-102">Método ICLRStrongName::StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="d77b5-102">ICLRStrongName::StrongNameGetBlobFromImage Method</span></span>
<span data-ttu-id="d77b5-103">Obtém uma representação binária da imagem do assembly no endereço de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="d77b5-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d77b5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d77b5-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d77b5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d77b5-105">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="d77b5-106">no O endereço de memória do manifesto do assembly mapeado.</span><span class="sxs-lookup"><span data-stu-id="d77b5-106">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="d77b5-107">no O tamanho, em bytes, da imagem em `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="d77b5-107">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="d77b5-108">no Um buffer para conter a representação binária da imagem.</span><span class="sxs-lookup"><span data-stu-id="d77b5-108">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="d77b5-109">[entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="d77b5-109">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="d77b5-110">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="d77b5-110">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d77b5-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d77b5-111">Return Value</span></span>  
 <span data-ttu-id="d77b5-112">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="d77b5-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d77b5-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d77b5-113">Requirements</span></span>  
 <span data-ttu-id="d77b5-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d77b5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d77b5-115">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="d77b5-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d77b5-116">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d77b5-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d77b5-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d77b5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77b5-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d77b5-118">See also</span></span>

- [<span data-ttu-id="d77b5-119">Método StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="d77b5-119">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="d77b5-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d77b5-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
