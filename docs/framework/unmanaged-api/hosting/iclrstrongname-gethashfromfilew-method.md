---
title: Método ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 8f2d74531233f2ba423c39126ddc43e499cbb5d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176364"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="fe5eb-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="fe5eb-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="fe5eb-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5eb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe5eb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="fe5eb-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fe5eb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="fe5eb-106">[em] O nome Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fe5eb-107">[dentro, fora] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="fe5eb-108">Algoritmos válidos são aqueles definidos pelo Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="fe5eb-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fe5eb-110">[fora] Uma matriz de byte contendo o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fe5eb-111">[em] O tamanho máximo do buffer `pbHash`apontado por .</span><span class="sxs-lookup"><span data-stu-id="fe5eb-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fe5eb-112">[fora] O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe5eb-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="fe5eb-113">Return Value</span></span>  
 <span data-ttu-id="fe5eb-114">`S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="fe5eb-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe5eb-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe5eb-115">Remarks</span></span>  
 <span data-ttu-id="fe5eb-116">Este método é o mesmo que o método [ICLRStrongName::GetHashFromFile,](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) exceto que a especificação do nome do arquivo é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="fe5eb-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5eb-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fe5eb-117">Requirements</span></span>  
 <span data-ttu-id="fe5eb-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5eb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5eb-119">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fe5eb-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fe5eb-120">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fe5eb-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe5eb-121">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5eb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5eb-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe5eb-122">See also</span></span>

- [<span data-ttu-id="fe5eb-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="fe5eb-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="fe5eb-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fe5eb-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
