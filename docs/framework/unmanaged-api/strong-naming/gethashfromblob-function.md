---
title: Função GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bfa846aa66345e23e085ca148c7e3f492c529f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576337"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="332b1-102">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="332b1-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="332b1-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="332b1-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="332b1-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="332b1-104">This function has been deprecated.</span></span> <span data-ttu-id="332b1-105">Use o [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="332b1-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="332b1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="332b1-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="332b1-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="332b1-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="332b1-108">[in] Um ponteiro para o endereço do bloco de memória a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="332b1-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="332b1-109">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="332b1-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="332b1-110">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="332b1-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="332b1-111">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="332b1-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="332b1-112">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="332b1-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="332b1-113">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="332b1-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="332b1-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="332b1-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="332b1-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="332b1-115">Requirements</span></span>  
 <span data-ttu-id="332b1-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="332b1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="332b1-117">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="332b1-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="332b1-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="332b1-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="332b1-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="332b1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="332b1-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="332b1-120">See also</span></span>
- [<span data-ttu-id="332b1-121">Método GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="332b1-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="332b1-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="332b1-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
