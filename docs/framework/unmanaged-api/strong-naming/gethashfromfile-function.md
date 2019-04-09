---
title: Função GetHashFromFile
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5774b7cdcfedfc407b626ab5052f5b4a77461e9b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155903"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="f2f44-102">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="f2f44-102">GetHashFromFile Function</span></span>
<span data-ttu-id="f2f44-103">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="f2f44-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="f2f44-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="f2f44-104">This function has been deprecated.</span></span> <span data-ttu-id="f2f44-105">Use o [iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f2f44-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f44-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2f44-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2f44-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2f44-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="f2f44-108">[in] O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="f2f44-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f2f44-109">[no, out] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="f2f44-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="f2f44-110">Algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="f2f44-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="f2f44-111">Se `piHashAlg` é definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="f2f44-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f2f44-112">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="f2f44-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f2f44-113">[in] O tamanho máximo do buffer que `pbHash` aponta.</span><span class="sxs-lookup"><span data-stu-id="f2f44-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f2f44-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f2f44-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2f44-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="f2f44-115">Remarks</span></span>  
 <span data-ttu-id="f2f44-116">Essa função é igual a [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="f2f44-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2f44-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2f44-117">Requirements</span></span>  
 <span data-ttu-id="f2f44-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2f44-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2f44-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f2f44-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f2f44-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f2f44-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="f2f44-121">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f2f44-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f2f44-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2f44-122">See also</span></span>

- [<span data-ttu-id="f2f44-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="f2f44-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="f2f44-124">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="f2f44-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="f2f44-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f2f44-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
