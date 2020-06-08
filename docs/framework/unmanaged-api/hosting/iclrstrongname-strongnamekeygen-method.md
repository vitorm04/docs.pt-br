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
ms.openlocfilehash: 69ba58cc8c5235a15749281b3107481be9528f84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503972"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a><span data-ttu-id="a6d72-102">Método ICLRStrongName::StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="a6d72-102">ICLRStrongName::StrongNameKeyGen Method</span></span>
<span data-ttu-id="a6d72-103">Cria um novo par de chaves públicas/privadas para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="a6d72-103">Creates a new public/private key pair for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6d72-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6d72-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6d72-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6d72-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a6d72-106">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="a6d72-106">[in] The requested key container name.</span></span> <span data-ttu-id="a6d72-107">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou NULL para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="a6d72-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a6d72-108">no Um valor que especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="a6d72-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="a6d72-109">Os seguintes valores têm suporte:</span><span class="sxs-lookup"><span data-stu-id="a6d72-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="a6d72-110">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="a6d72-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="a6d72-111">0x00000001 ( `SN_LEAVE_KEY` ) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="a6d72-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="a6d72-112">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="a6d72-112">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="a6d72-113">fora O tamanho, em bytes, de `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="a6d72-113">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6d72-114">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="a6d72-114">Return Value</span></span>  
 <span data-ttu-id="a6d72-115">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="a6d72-115">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6d72-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6d72-116">Remarks</span></span>  
 <span data-ttu-id="a6d72-117">O método [ICLRStrongName:: StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="a6d72-117">The [ICLRStrongName::StrongNameKeyGen](iclrstrongname-strongnamekeygen-method.md) method creates a 1024-bit key.</span></span> <span data-ttu-id="a6d72-118">Depois que a chave for recuperada, você deverá chamar o método [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="a6d72-118">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6d72-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6d72-119">Requirements</span></span>  
 <span data-ttu-id="a6d72-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6d72-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6d72-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="a6d72-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a6d72-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a6d72-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6d72-123">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6d72-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6d72-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a6d72-124">See also</span></span>

- [<span data-ttu-id="a6d72-125">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="a6d72-125">StrongNameKeyGenEx Method</span></span>](iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="a6d72-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a6d72-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
