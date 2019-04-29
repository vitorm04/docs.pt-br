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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767501"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="9c0a3-102">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="9c0a3-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="9c0a3-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="9c0a3-104">`StrongNameSignatureSize` normalmente é usado por compiladores para determinar a quantidade de espaço para reservar no arquivo durante a criação de um assembly assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="9c0a3-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-105">This function has been deprecated.</span></span> <span data-ttu-id="9c0a3-106">Use o [iclrstrongname:: Strongnamesignaturesize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0a3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9c0a3-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9c0a3-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9c0a3-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="9c0a3-109">[in] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="9c0a3-110">[in] O tamanho, em bytes, do `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="9c0a3-111">[in] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c0a3-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9c0a3-112">Return Value</span></span>  
 <span data-ttu-id="9c0a3-113">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c0a3-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="9c0a3-114">Remarks</span></span>  
 <span data-ttu-id="9c0a3-115">Se o `StrongNameSignatureSize` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="9c0a3-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0a3-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9c0a3-116">Requirements</span></span>  
 <span data-ttu-id="9c0a3-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c0a3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c0a3-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9c0a3-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9c0a3-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9c0a3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c0a3-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c0a3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0a3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c0a3-121">See also</span></span>

- [<span data-ttu-id="9c0a3-122">Método StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="9c0a3-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="9c0a3-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9c0a3-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
