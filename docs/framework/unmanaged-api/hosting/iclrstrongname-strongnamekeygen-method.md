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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a70a23e6c6e219b76ccfee6cecdccf7ed0533e75
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584617"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="62dec-102">Método ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="62dec-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="62dec-103">Cria um novo par de chaves públicas/privadas para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="62dec-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62dec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62dec-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62dec-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="62dec-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="62dec-106">[in] O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="62dec-106">[in] The requested key container name.</span></span> <span data-ttu-id="62dec-107">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou null para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="62dec-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="62dec-108">[in] Um valor que especifica se é necessário deixar a chave registrado.</span><span class="sxs-lookup"><span data-stu-id="62dec-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="62dec-109">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="62dec-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="62dec-110">0x00000000 - usado quando `wszKeyContainer` é nula para gerar um nome de contêiner de chave temporária.</span><span class="sxs-lookup"><span data-stu-id="62dec-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="62dec-111">0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="62dec-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="62dec-112">[out] O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="62dec-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="62dec-113">[out] O tamanho, em bytes, do `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="62dec-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62dec-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="62dec-114">Return Value</span></span>  
 <span data-ttu-id="62dec-115">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="62dec-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62dec-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="62dec-116">Remarks</span></span>  
 <span data-ttu-id="62dec-117">O [iclrstrongname:: Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) método cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="62dec-117">The [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="62dec-118">Após a chave de recuperação, você deve chamar o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="62dec-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62dec-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62dec-119">Requirements</span></span>  
 <span data-ttu-id="62dec-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62dec-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62dec-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="62dec-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="62dec-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="62dec-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62dec-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62dec-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62dec-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62dec-124">See also</span></span>

- [<span data-ttu-id="62dec-125">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="62dec-125">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="62dec-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="62dec-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
