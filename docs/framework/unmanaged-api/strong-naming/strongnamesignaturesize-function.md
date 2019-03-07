---
title: Função StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dac6f2ca813f3b8cbed48d540a991e6396edf679
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495215"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="fb682-102">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="fb682-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="fb682-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="fb682-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="fb682-104">`StrongNameSignatureSize` normalmente é usado por compiladores para determinar a quantidade de espaço para reservar no arquivo durante a criação de um assembly assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="fb682-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="fb682-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="fb682-105">This function has been deprecated.</span></span> <span data-ttu-id="fb682-106">Use o [iclrstrongname:: Strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="fb682-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb682-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb682-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="fb682-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb682-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="fb682-109">[in] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="fb682-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="fb682-110">[in] O tamanho, em bytes, do `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="fb682-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="fb682-111">[in] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="fb682-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb682-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fb682-112">Return Value</span></span>  
 <span data-ttu-id="fb682-113">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="fb682-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb682-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb682-114">Remarks</span></span>  
 <span data-ttu-id="fb682-115">Se o `StrongNameSignatureSize` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="fb682-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb682-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb682-116">Requirements</span></span>  
 <span data-ttu-id="fb682-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb682-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb682-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="fb682-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="fb682-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fb682-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb682-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb682-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb682-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb682-121">See also</span></span>
- [<span data-ttu-id="fb682-122">Método StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="fb682-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="fb682-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fb682-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
