---
title: Função StrongNameKeyGenEx
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
ms.openlocfilehash: 63ddd90f3a8090853d10f03052915d10e1503ea6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125213"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="bbbe8-102">Função StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="bbbe8-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="bbbe8-103">Gera um novo par de chaves pública/privada com o tamanho de chave especificado, para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="bbbe8-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-104">This function has been deprecated.</span></span> <span data-ttu-id="bbbe8-105">Em vez disso, use o método [ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bbbe8-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbbe8-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbbe8-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbbe8-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbbe8-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="bbbe8-108">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-108">[in] The requested key container name.</span></span> <span data-ttu-id="bbbe8-109">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou nula para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bbbe8-110">no Especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="bbbe8-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="bbbe8-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="bbbe8-112">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="bbbe8-113">0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="bbbe8-114">no O tamanho solicitado da chave, em bits.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="bbbe8-115">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="bbbe8-116">fora O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbbe8-117">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="bbbe8-117">Return Value</span></span>  
 <span data-ttu-id="bbbe8-118">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbbe8-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbbe8-119">Remarks</span></span>  
 <span data-ttu-id="bbbe8-120">As versões 1,0 e 1,1 do .NET Framework exigem uma `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2,0 adiciona suporte para chaves de 2048 bits.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="bbbe8-121">Depois que a chave for recuperada, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="bbbe8-122">Se a função `StrongNameKeyGenEx` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="bbbe8-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbbe8-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbbe8-123">Requirements</span></span>  
 <span data-ttu-id="bbbe8-124">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbbe8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbbe8-125">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bbbe8-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bbbe8-126">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bbbe8-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bbbe8-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbbe8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbe8-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbbe8-128">See also</span></span>

- [<span data-ttu-id="bbbe8-129">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="bbbe8-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="bbbe8-130">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="bbbe8-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="bbbe8-131">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bbbe8-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
