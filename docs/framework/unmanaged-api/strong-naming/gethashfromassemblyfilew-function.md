---
title: Função GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772054"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="6bae4-102">Função GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="6bae4-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="6bae4-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="6bae4-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="6bae4-104">O caminho para o arquivo do assembly deve ser especificado como uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bae4-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="6bae4-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="6bae4-105">This function has been deprecated.</span></span> <span data-ttu-id="6bae4-106">Use o [iclrstrongname:: Gethashfromassemblyfilew](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6bae4-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bae4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bae4-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bae4-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bae4-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6bae4-109">[in] O caminho para o arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="6bae4-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="6bae4-110">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bae4-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6bae4-111">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="6bae4-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6bae4-112">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="6bae4-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6bae4-113">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="6bae4-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6bae4-114">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6bae4-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6bae4-115">[out] O retornado tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6bae4-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bae4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bae4-116">Requirements</span></span>  
 <span data-ttu-id="6bae4-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bae4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bae4-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6bae4-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6bae4-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6bae4-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bae4-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bae4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bae4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bae4-121">See also</span></span>

- [<span data-ttu-id="6bae4-122">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="6bae4-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="6bae4-123">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="6bae4-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="6bae4-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6bae4-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
