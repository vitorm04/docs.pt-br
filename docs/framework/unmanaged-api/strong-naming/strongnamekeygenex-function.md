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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9ab908866402bd7a883114466f32921321a5ee6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799004"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="cbb82-102">Função StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="cbb82-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="cbb82-103">Gera um novo par de chaves pública/privada com o tamanho de chave especificado, para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="cbb82-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="cbb82-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="cbb82-104">This function has been deprecated.</span></span> <span data-ttu-id="cbb82-105">Em vez disso, use o método [ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cbb82-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb82-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cbb82-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbb82-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cbb82-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="cbb82-108">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="cbb82-108">[in] The requested key container name.</span></span> <span data-ttu-id="cbb82-109">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia ou NULL para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="cbb82-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cbb82-110">no Especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="cbb82-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="cbb82-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="cbb82-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="cbb82-112">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="cbb82-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="cbb82-113">0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="cbb82-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="cbb82-114">no O tamanho solicitado da chave, em bits.</span><span class="sxs-lookup"><span data-stu-id="cbb82-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="cbb82-115">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="cbb82-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="cbb82-116">fora O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="cbb82-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cbb82-117">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="cbb82-117">Return Value</span></span>  
 <span data-ttu-id="cbb82-118">`true`após a conclusão bem-sucedida; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="cbb82-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbb82-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="cbb82-119">Remarks</span></span>  
 <span data-ttu-id="cbb82-120">O .NET Framework versões 1,0 e 1,1 exigem um `dwKeySize` de 1024 bits para assinar um assembly com um nome forte; a versão 2,0 adiciona suporte para chaves de bits de 2048.</span><span class="sxs-lookup"><span data-stu-id="cbb82-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="cbb82-121">Depois que a chave for recuperada, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="cbb82-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="cbb82-122">Se a `StrongNameKeyGenEx` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="cbb82-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb82-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cbb82-123">Requirements</span></span>  
 <span data-ttu-id="cbb82-124">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb82-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb82-125">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cbb82-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cbb82-126">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cbb82-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cbb82-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbb82-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbb82-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cbb82-128">See also</span></span>

- [<span data-ttu-id="cbb82-129">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="cbb82-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="cbb82-130">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="cbb82-130">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="cbb82-131">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="cbb82-131">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
