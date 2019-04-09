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
ms.openlocfilehash: 01c0f9ca0299e817618d93133c0eaca9fc63788e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160310"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="c8a7b-102">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="c8a7b-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="c8a7b-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-103">Returns the size of the strong name signature.</span></span> `StrongNameSignatureSize` <span data-ttu-id="c8a7b-104">normalmente é usado por compiladores para determinar a quantidade de espaço para reservar no arquivo durante a criação de um assembly assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-104">is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="c8a7b-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-105">This function has been deprecated.</span></span> <span data-ttu-id="c8a7b-106">Use o [iclrstrongname:: Strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8a7b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c8a7b-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c8a7b-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c8a7b-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="c8a7b-109">[in] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="c8a7b-110">[in] O tamanho, em bytes, do `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c8a7b-111">[in] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8a7b-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c8a7b-112">Return Value</span></span>  
 `true` <span data-ttu-id="c8a7b-113">Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-113">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8a7b-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c8a7b-114">Remarks</span></span>  
 <span data-ttu-id="c8a7b-115">Se o `StrongNameSignatureSize` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="c8a7b-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8a7b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c8a7b-116">Requirements</span></span>  
 <span data-ttu-id="c8a7b-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8a7b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8a7b-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c8a7b-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c8a7b-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c8a7b-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c8a7b-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c8a7b-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c8a7b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8a7b-121">See also</span></span>

- [<span data-ttu-id="c8a7b-122">Método StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="c8a7b-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="c8a7b-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c8a7b-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
