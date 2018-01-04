---
title: "Método ICLRStrongName::StrongNameGetBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1882936723667b616ff930af00ee899f446521e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="7799d-102">Método ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="7799d-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="7799d-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="7799d-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7799d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7799d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7799d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7799d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7799d-106">[in] Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="7799d-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="7799d-107">[in] O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="7799d-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="7799d-108">[out no] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7799d-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="7799d-109">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="7799d-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7799d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7799d-110">Return Value</span></span>  
 <span data-ttu-id="7799d-111">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="7799d-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7799d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7799d-112">Requirements</span></span>  
 <span data-ttu-id="7799d-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7799d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7799d-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7799d-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7799d-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7799d-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7799d-116">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7799d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7799d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7799d-117">See Also</span></span>  
 [<span data-ttu-id="7799d-118">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="7799d-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="7799d-119">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7799d-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
