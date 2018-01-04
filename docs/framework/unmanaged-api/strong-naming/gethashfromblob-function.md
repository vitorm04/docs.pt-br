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
ms.workload: dotnet
ms.openlocfilehash: 4564ea36ed8dd4c5de0d1633ba791b47bc2a01b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="389a4-102">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="389a4-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="389a4-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="389a4-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="389a4-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="389a4-104">This function has been deprecated.</span></span> <span data-ttu-id="389a4-105">Use o [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="389a4-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="389a4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="389a4-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="389a4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="389a4-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="389a4-108">[in] Um ponteiro para o endereço do bloco de memória a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="389a4-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="389a4-109">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="389a4-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="389a4-110">[out no] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="389a4-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="389a4-111">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="389a4-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="389a4-112">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="389a4-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="389a4-113">[in] O tamanho máximo solicitado da `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="389a4-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="389a4-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="389a4-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="389a4-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="389a4-115">Requirements</span></span>  
 <span data-ttu-id="389a4-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="389a4-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="389a4-117">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="389a4-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="389a4-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="389a4-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="389a4-119">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="389a4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="389a4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="389a4-120">See Also</span></span>  
 [<span data-ttu-id="389a4-121">Método GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="389a4-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="389a4-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="389a4-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
