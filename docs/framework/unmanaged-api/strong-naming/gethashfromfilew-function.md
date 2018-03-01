---
title: "Função GetHashFromFileW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d7d62526a6ac9bb06a7de8287c9687933402bfb8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="e8e31-102">Função GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e8e31-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="e8e31-103">Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8e31-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="e8e31-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="e8e31-104">This function has been deprecated.</span></span> <span data-ttu-id="e8e31-105">Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e8e31-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e31-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8e31-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8e31-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8e31-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e8e31-108">[in] O nome de Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="e8e31-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e8e31-109">[out no] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="e8e31-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e8e31-110">Os algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="e8e31-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e8e31-111">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="e8e31-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e8e31-112">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="e8e31-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e8e31-113">[in] O tamanho máximo do buffer apontado pelo `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e8e31-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e8e31-114">[out] O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e8e31-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8e31-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e8e31-115">Remarks</span></span>  
 <span data-ttu-id="e8e31-116">Essa função é o mesmo que [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), exceto que a especificação de nome de arquivo for Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="e8e31-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8e31-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8e31-117">Requirements</span></span>  
 <span data-ttu-id="e8e31-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e31-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e31-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e8e31-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e8e31-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e8e31-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8e31-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e31-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e31-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8e31-122">See Also</span></span>  
 [<span data-ttu-id="e8e31-123">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e8e31-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="e8e31-124">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="e8e31-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="e8e31-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e8e31-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
