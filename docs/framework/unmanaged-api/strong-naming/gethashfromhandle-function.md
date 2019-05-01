---
title: Função GetHashFromHandle
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48dd987896536006fe81bc01528cadb507123e27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049421"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="5402f-102">Função GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="5402f-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="5402f-103">Gera um hash sobre o conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="5402f-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="5402f-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="5402f-104">This function has been deprecated.</span></span> <span data-ttu-id="5402f-105">Use o [iclrstrongname:: Gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="5402f-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5402f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5402f-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5402f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5402f-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="5402f-108">[in] O identificador do arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="5402f-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="5402f-109">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="5402f-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="5402f-110">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="5402f-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="5402f-111">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="5402f-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="5402f-112">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5402f-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="5402f-113">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="5402f-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5402f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5402f-114">Requirements</span></span>  
 <span data-ttu-id="5402f-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5402f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5402f-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="5402f-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="5402f-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5402f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5402f-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5402f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5402f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5402f-119">See also</span></span>

- [<span data-ttu-id="5402f-120">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="5402f-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="5402f-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="5402f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
