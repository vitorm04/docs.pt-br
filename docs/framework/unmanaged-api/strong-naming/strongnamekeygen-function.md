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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fce08434cb8864350fd333dcfcaa388a8031c09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459160"
---
# <a name="strongnamekeygen-function"></a><span data-ttu-id="27156-102">Função StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="27156-102">StrongNameKeyGen Function</span></span>
<span data-ttu-id="27156-103">Cria um novo par de chaves pública/privada para uso de nome forte.</span><span class="sxs-lookup"><span data-stu-id="27156-103">Creates a new public/private key pair for strong name use.</span></span>  
  
 <span data-ttu-id="27156-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="27156-104">This function has been deprecated.</span></span> <span data-ttu-id="27156-105">Use o [Strongnamekeygen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="27156-105">Use the [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27156-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27156-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27156-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27156-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="27156-108">[in] O nome do contêiner de chave solicitado.</span><span class="sxs-lookup"><span data-stu-id="27156-108">[in] The requested key container name.</span></span> <span data-ttu-id="27156-109">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia ou null para gerar um nome temporário.</span><span class="sxs-lookup"><span data-stu-id="27156-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="27156-110">[in] Especifica se deve deixar a chave registrada.</span><span class="sxs-lookup"><span data-stu-id="27156-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="27156-111">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="27156-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="27156-112">0x00000000 - usado quando `wszKeyContainer` é nulo para gerar um nome de contêiner de chave temporária.</span><span class="sxs-lookup"><span data-stu-id="27156-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="27156-113">0x00000001 (`SN_LEAVE_KEY`)-Especifica que a chave deve ser registrada para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="27156-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="27156-114">[out] O par de chaves pública/privada retornado.</span><span class="sxs-lookup"><span data-stu-id="27156-114">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="27156-115">[out] O tamanho, em bytes, de `ppbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="27156-115">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27156-116">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="27156-116">Return Value</span></span>  
 <span data-ttu-id="27156-117">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="27156-117">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27156-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="27156-118">Remarks</span></span>  
 <span data-ttu-id="27156-119">O `StrongNameKeyGen` função cria uma chave de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="27156-119">The `StrongNameKeyGen` function creates a 1024-bit key.</span></span> <span data-ttu-id="27156-120">Após a chave de recuperação, você deve chamar o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="27156-120">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="27156-121">Se o `StrongNameKeyGen` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="27156-121">If the `StrongNameKeyGen` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27156-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27156-122">Requirements</span></span>  
 <span data-ttu-id="27156-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27156-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27156-124">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="27156-124">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="27156-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="27156-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="27156-126">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27156-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27156-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27156-127">See Also</span></span>  
 [<span data-ttu-id="27156-128">Método StrongNameKeyGen</span><span class="sxs-lookup"><span data-stu-id="27156-128">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [<span data-ttu-id="27156-129">Método StrongNameKeyGenEx</span><span class="sxs-lookup"><span data-stu-id="27156-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [<span data-ttu-id="27156-130">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="27156-130">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
