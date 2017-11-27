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
ms.openlocfilehash: bc7589e2a977502a3e75a95b8a065f45b8805072
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="343cd-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="343cd-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="343cd-103">Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="343cd-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="343cd-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="343cd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="343cd-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="343cd-106">[in] O nome de Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="343cd-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="343cd-107">[out no] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="343cd-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="343cd-108">Os algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="343cd-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="343cd-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="343cd-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="343cd-110">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="343cd-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="343cd-111">[in] O tamanho máximo do buffer apontado pelo `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="343cd-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="343cd-112">[out] O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="343cd-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="343cd-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="343cd-113">Return Value</span></span>  
 <span data-ttu-id="343cd-114">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="343cd-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="343cd-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="343cd-115">Remarks</span></span>  
 <span data-ttu-id="343cd-116">Esse método é o mesmo que o [Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que o nome do arquivo especificação é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="343cd-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343cd-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="343cd-117">Requirements</span></span>  
 <span data-ttu-id="343cd-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="343cd-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="343cd-119">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="343cd-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="343cd-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="343cd-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="343cd-121">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="343cd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343cd-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="343cd-122">See Also</span></span>  
 [<span data-ttu-id="343cd-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="343cd-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)  
 [<span data-ttu-id="343cd-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="343cd-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
