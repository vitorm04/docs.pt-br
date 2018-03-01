---
title: "Função GetHashFromFile"
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
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be7979eb0f7d32e02257cc0b3cb400263350f0bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="a6bca-102">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="a6bca-102">GetHashFromFile Function</span></span>
<span data-ttu-id="a6bca-103">Gera um hash com base no conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="a6bca-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="a6bca-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="a6bca-104">This function has been deprecated.</span></span> <span data-ttu-id="a6bca-105">Use o [Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a6bca-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6bca-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6bca-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6bca-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6bca-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="a6bca-108">[in] O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="a6bca-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="a6bca-109">[out no] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="a6bca-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="a6bca-110">Os algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="a6bca-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="a6bca-111">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="a6bca-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="a6bca-112">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="a6bca-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="a6bca-113">[in] O tamanho máximo do buffer que `pbHash` aponta para.</span><span class="sxs-lookup"><span data-stu-id="a6bca-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="a6bca-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="a6bca-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6bca-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6bca-115">Remarks</span></span>  
 <span data-ttu-id="a6bca-116">Essa função é o mesmo que [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="a6bca-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6bca-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6bca-117">Requirements</span></span>  
 <span data-ttu-id="a6bca-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6bca-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6bca-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a6bca-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a6bca-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a6bca-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6bca-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6bca-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6bca-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6bca-122">See Also</span></span>  
 [<span data-ttu-id="a6bca-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="a6bca-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="a6bca-124">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="a6bca-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="a6bca-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="a6bca-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
