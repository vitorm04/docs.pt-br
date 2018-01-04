---
title: "Método ICLRStrongName::StrongNameSignatureSize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureSize
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="4ab76-102">Método ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="4ab76-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="4ab76-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="4ab76-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="4ab76-104">Esse método é normalmente usado por compiladores para determinar a quantidade de espaço para reservar o arquivo durante a criação de um assembly assinado com atraso.</span><span class="sxs-lookup"><span data-stu-id="4ab76-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab76-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ab76-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ab76-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ab76-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="4ab76-107">[in] Uma estrutura de tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="4ab76-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="4ab76-108">[in] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="4ab76-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="4ab76-109">[in] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="4ab76-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab76-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ab76-110">Return Value</span></span>  
 <span data-ttu-id="4ab76-111">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="4ab76-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab76-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ab76-112">Requirements</span></span>  
 <span data-ttu-id="4ab76-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab76-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4ab76-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4ab76-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4ab76-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ab76-116">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab76-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab76-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ab76-117">See Also</span></span>  
 [<span data-ttu-id="4ab76-118">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="4ab76-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
