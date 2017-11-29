---
title: "Função GetHashFromBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetHashFromBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetHashFromBlob
helpviewer_keywords: GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 360036cd1578c2845f09f92c09d79e44618abe75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="d8097-102">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="d8097-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="d8097-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="d8097-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="d8097-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="d8097-104">This function has been deprecated.</span></span> <span data-ttu-id="d8097-105">Use o [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="d8097-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8097-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8097-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8097-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8097-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="d8097-108">[in] Um ponteiro para o endereço do bloco de memória a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="d8097-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="d8097-109">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="d8097-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="d8097-110">[out no] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="d8097-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="d8097-111">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="d8097-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="d8097-112">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="d8097-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="d8097-113">[in] O tamanho máximo solicitado da `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d8097-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="d8097-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="d8097-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8097-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8097-115">Requirements</span></span>  
 <span data-ttu-id="d8097-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8097-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8097-117">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="d8097-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="d8097-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="d8097-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8097-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8097-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8097-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8097-120">See Also</span></span>  
 [<span data-ttu-id="d8097-121">Método GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="d8097-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="d8097-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="d8097-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
