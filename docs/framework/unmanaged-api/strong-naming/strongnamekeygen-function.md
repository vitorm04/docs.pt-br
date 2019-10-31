---
title: Função StrongNameKeyGen
ms.date: 03/30/2017
api_name:
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
ms.openlocfilehash: 79b2235e3645c89c2cd9ebcce079d5eb7efdd162
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128747"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="07883-102">Função StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="07883-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="07883-103">Cria um novo par de chaves públicas/privadas para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="07883-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="07883-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="07883-104">This function has been deprecated.</span></span> <span data-ttu-id="07883-105">Em vez disso, use o método [ICLRStrongName:: StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) .</span><span class="sxs-lookup"><span data-stu-id="07883-105">Use the [ICLRStrongName::StrongNameKeyGen](../hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07883-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07883-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07883-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="07883-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="07883-108">no O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="07883-108">[in] The requested key container name.</span></span> <span data-ttu-id="07883-109">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou nula para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="07883-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="07883-110">no Especifica se a chave deve ser desregistrada.</span><span class="sxs-lookup"><span data-stu-id="07883-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="07883-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="07883-111">The following values are supported:</span></span>  
  
- <span data-ttu-id="07883-112">0x00000000-usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporário.</span><span class="sxs-lookup"><span data-stu-id="07883-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
- <span data-ttu-id="07883-113">0x00000001 (`SN_LEAVE_KEY`) – especifica que a chave deve ser registrada.</span><span class="sxs-lookup"><span data-stu-id="07883-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="07883-114">fora O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="07883-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="07883-115">fora O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="07883-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07883-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="07883-116">Return Value</span></span>  
 <span data-ttu-id="07883-117">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="07883-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07883-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="07883-118">Remarks</span></span>  
 <span data-ttu-id="07883-119">A função `StrongNameKeyGen` cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="07883-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="07883-120">Depois que a chave for recuperada, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="07883-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="07883-121">Se a função `StrongNameKeyGen` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="07883-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07883-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="07883-122">Requirements</span></span>  
 <span data-ttu-id="07883-123">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07883-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07883-124">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="07883-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="07883-125">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="07883-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="07883-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07883-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07883-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07883-127">See also</span></span>

- [<span data-ttu-id="07883-128">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="07883-128">StrongNameKeyGen Method</span></span>](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="07883-129">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="07883-129">StrongNameKeyGenEx Method</span></span>](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="07883-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="07883-130">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
