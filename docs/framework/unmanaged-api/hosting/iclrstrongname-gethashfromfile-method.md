---
title: "Método ICLRStrongName::GetHashFromFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 480113148e039ff1be3e438b4af2e24fdeacba14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="e5b63-102">Método ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="e5b63-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="e5b63-103">Gera um hash com base no conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="e5b63-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e5b63-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e5b63-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5b63-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="e5b63-106">[in] O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="e5b63-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e5b63-107">[out no] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="e5b63-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e5b63-108">Os algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="e5b63-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e5b63-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="e5b63-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e5b63-110">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="e5b63-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e5b63-111">[in] O tamanho máximo do buffer que `pbHash` aponta para.</span><span class="sxs-lookup"><span data-stu-id="e5b63-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e5b63-112">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e5b63-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e5b63-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e5b63-113">Return Value</span></span>  
 <span data-ttu-id="e5b63-114">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="e5b63-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5b63-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e5b63-115">Remarks</span></span>  
 <span data-ttu-id="e5b63-116">Esse método é o mesmo que o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) , exceto que o nome do arquivo especificação é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5b63-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b63-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e5b63-117">Requirements</span></span>  
 <span data-ttu-id="e5b63-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5b63-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5b63-119">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e5b63-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e5b63-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e5b63-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e5b63-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5b63-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b63-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5b63-122">See Also</span></span>  
 [<span data-ttu-id="e5b63-123">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e5b63-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)  
 [<span data-ttu-id="e5b63-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e5b63-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
