---
title: "Função StrongNameSignatureSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameSignatureSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameSignatureSize
helpviewer_keywords: StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7944763f1c1379228e715b18b563e7aa776fedac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="462d5-102">Função StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="462d5-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="462d5-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="462d5-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="462d5-104">`StrongNameSignatureSize`normalmente é usado por compiladores para determinar a quantidade de espaço para reservar o arquivo durante a criação de um assembly assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="462d5-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="462d5-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="462d5-105">This function has been deprecated.</span></span> <span data-ttu-id="462d5-106">Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="462d5-106">Use the [ICLRStrongName::StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="462d5-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="462d5-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="462d5-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="462d5-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="462d5-109">[in] Uma estrutura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="462d5-109">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="462d5-110">[in] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="462d5-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="462d5-111">[in] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="462d5-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="462d5-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="462d5-112">Return Value</span></span>  
 <span data-ttu-id="462d5-113">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="462d5-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="462d5-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="462d5-114">Remarks</span></span>  
 <span data-ttu-id="462d5-115">Se o `StrongNameSignatureSize` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="462d5-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="462d5-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="462d5-116">Requirements</span></span>  
 <span data-ttu-id="462d5-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="462d5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="462d5-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="462d5-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="462d5-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="462d5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="462d5-120">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="462d5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462d5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="462d5-121">See Also</span></span>  
 [<span data-ttu-id="462d5-122">Método StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="462d5-122">StrongNameSignatureSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)  
 [<span data-ttu-id="462d5-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="462d5-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
