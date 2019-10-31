---
title: Método ICLRStrongName::StrongNameKeyGen
ms.date: 03/30/2017
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
ms.openlocfilehash: 4f3574e282d24fa11ffa2f85463f682c42098ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135045"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="ff1c1-102">Método ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="ff1c1-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="ff1c1-103">Cria um novo par de chaves públicas/privadas para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff1c1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff1c1-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff1c1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ff1c1-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ff1c1-106">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-106">[in] The requested key container name.</span></span> <span data-ttu-id="ff1c1-107">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou nula para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ff1c1-108">no Um valor que especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="ff1c1-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="ff1c1-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="ff1c1-110">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="ff1c1-111">0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="ff1c1-112">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="ff1c1-113">fora O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff1c1-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ff1c1-114">Return Value</span></span>  
 <span data-ttu-id="ff1c1-115">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="ff1c1-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff1c1-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff1c1-116">Remarks</span></span>  
 <span data-ttu-id="ff1c1-117">O método [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="ff1c1-118">Depois que a chave for recuperada, você deverá chamar o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="ff1c1-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff1c1-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ff1c1-119">Requirements</span></span>  
 <span data-ttu-id="ff1c1-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff1c1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff1c1-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ff1c1-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ff1c1-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ff1c1-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff1c1-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff1c1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff1c1-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff1c1-124">See also</span></span>

- [<span data-ttu-id="ff1c1-125">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="ff1c1-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="ff1c1-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ff1c1-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
