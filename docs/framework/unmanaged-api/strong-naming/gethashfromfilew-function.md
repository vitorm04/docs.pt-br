---
title: Função GetHashFromFileW
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 611da2dcb5686f79207e5099661fbbf5e7981421
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681918"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="25b78-102">Função GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="25b78-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="25b78-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="25b78-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="25b78-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="25b78-104">This function has been deprecated.</span></span> <span data-ttu-id="25b78-105">Use o [iclrstrongname:: Gethashfromfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="25b78-105">Use the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b78-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25b78-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="25b78-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="25b78-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="25b78-108">[in] O nome do Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="25b78-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="25b78-109">[no, out] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="25b78-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="25b78-110">Algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="25b78-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="25b78-111">Se `piHashAlg` é definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="25b78-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="25b78-112">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="25b78-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="25b78-113">[in] O tamanho máximo do buffer apontado por `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="25b78-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="25b78-114">[out] O tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="25b78-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25b78-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="25b78-115">Remarks</span></span>  
 <span data-ttu-id="25b78-116">Essa função é igual a [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="25b78-116">This function is the same as [GetHashFromFile](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b78-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25b78-117">Requirements</span></span>  
 <span data-ttu-id="25b78-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b78-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b78-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="25b78-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="25b78-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="25b78-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25b78-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b78-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b78-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25b78-122">See also</span></span>
- [<span data-ttu-id="25b78-123">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="25b78-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="25b78-124">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="25b78-124">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="25b78-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="25b78-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
