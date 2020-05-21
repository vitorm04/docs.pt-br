---
title: Método ICLRStrongName::StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGenEx
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyGenEx method [.NET Framework hosting]
- StrongNameKeyGenEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 1f8b59d0-5b72-45b8-ab74-c2b43ffc806e
topic_type:
- apiref
ms.openlocfilehash: fb18b7b5ac73a1f270af6fae95a23e04b17ca5f1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763066"
---
# <a name="iclrstrongnamestrongnamekeygenex-method"></a><span data-ttu-id="87d0f-102">Método ICLRStrongName::StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="87d0f-102">ICLRStrongName::StrongNameKeyGenEx Method</span></span>
<span data-ttu-id="87d0f-103">Gera um novo par de chaves pública/privada com o tamanho de chave especificado, para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="87d0f-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87d0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87d0f-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87d0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87d0f-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="87d0f-106">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="87d0f-106">[in] The requested key container name.</span></span> <span data-ttu-id="87d0f-107">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou NULL para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="87d0f-107">`wszKeyContainer` must either be a non-empty string or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="87d0f-108">no Um valor que especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="87d0f-108">[in] A value that specifies whether to leave the key registered.</span></span> <span data-ttu-id="87d0f-109">Os valores a seguir têm suporte:</span><span class="sxs-lookup"><span data-stu-id="87d0f-109">The following values are supported:</span></span>  
  
- <span data-ttu-id="87d0f-110">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="87d0f-110">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="87d0f-111">0x00000001 ( `SN_LEAVE_KEY` ) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="87d0f-111">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="87d0f-112">no O tamanho solicitado da chave, em bits.</span><span class="sxs-lookup"><span data-stu-id="87d0f-112">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="87d0f-113">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="87d0f-113">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="87d0f-114">fora O tamanho, em bytes, de `ppbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="87d0f-114">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87d0f-115">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="87d0f-115">Return Value</span></span>  
 <span data-ttu-id="87d0f-116">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="87d0f-116">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87d0f-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="87d0f-117">Remarks</span></span>  
 <span data-ttu-id="87d0f-118">O .NET Framework versões 1,0 e 1,1 exigem um `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2,0 adiciona suporte para chaves de bits de 2048.</span><span class="sxs-lookup"><span data-stu-id="87d0f-118">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="87d0f-119">Depois que a chave for recuperada, você deverá chamar o método [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="87d0f-119">After the key is retrieved, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87d0f-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87d0f-120">Requirements</span></span>  
 <span data-ttu-id="87d0f-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87d0f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87d0f-122">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="87d0f-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="87d0f-123">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87d0f-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87d0f-124">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87d0f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d0f-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="87d0f-125">See also</span></span>

- [<span data-ttu-id="87d0f-126">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="87d0f-126">StrongNameKeyGen Method</span></span>](iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="87d0f-127">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="87d0f-127">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
