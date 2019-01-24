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
ms.openlocfilehash: e81ed965fcd5c293378bcffd943eecff35257013
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572663"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="eea5a-102">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="eea5a-102">GetHashFromFile Function</span></span>
<span data-ttu-id="eea5a-103">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="eea5a-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="eea5a-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="eea5a-104">This function has been deprecated.</span></span> <span data-ttu-id="eea5a-105">Use o [iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="eea5a-105">Use the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eea5a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eea5a-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eea5a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eea5a-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="eea5a-108">[in] O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="eea5a-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="eea5a-109">[no, out] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="eea5a-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="eea5a-110">Algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="eea5a-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="eea5a-111">Se `piHashAlg` é definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="eea5a-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="eea5a-112">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="eea5a-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="eea5a-113">[in] O tamanho máximo do buffer que `pbHash` aponta.</span><span class="sxs-lookup"><span data-stu-id="eea5a-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="eea5a-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="eea5a-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eea5a-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="eea5a-115">Remarks</span></span>  
 <span data-ttu-id="eea5a-116">Essa função é igual a [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="eea5a-116">This function is the same as [GetHashFromFileW](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eea5a-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eea5a-117">Requirements</span></span>  
 <span data-ttu-id="eea5a-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eea5a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eea5a-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="eea5a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="eea5a-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="eea5a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eea5a-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eea5a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea5a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eea5a-122">See also</span></span>
- [<span data-ttu-id="eea5a-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="eea5a-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="eea5a-124">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="eea5a-124">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="eea5a-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="eea5a-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
