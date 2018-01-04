---
title: "Método ICLRStrongName::GetHashFromFileW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.GetHashFromFileW
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec58e0cf062e405c757a506e9c26955009b710b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="e2d49-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="e2d49-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="e2d49-103">Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="e2d49-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2d49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2d49-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2d49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e2d49-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e2d49-106">[in] O nome de Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="e2d49-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e2d49-107">[out no] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="e2d49-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="e2d49-108">Os algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="e2d49-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="e2d49-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="e2d49-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e2d49-110">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="e2d49-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e2d49-111">[in] O tamanho máximo do buffer apontado pelo `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e2d49-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e2d49-112">[out] O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e2d49-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2d49-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e2d49-113">Return Value</span></span>  
 <span data-ttu-id="e2d49-114">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="e2d49-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2d49-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="e2d49-115">Remarks</span></span>  
 <span data-ttu-id="e2d49-116">Esse método é o mesmo que o [Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que o nome do arquivo especificação é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="e2d49-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2d49-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2d49-117">Requirements</span></span>  
 <span data-ttu-id="e2d49-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2d49-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2d49-119">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e2d49-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e2d49-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e2d49-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2d49-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2d49-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d49-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2d49-122">See Also</span></span>  
 [<span data-ttu-id="e2d49-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="e2d49-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="e2d49-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e2d49-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
