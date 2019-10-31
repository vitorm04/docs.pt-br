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
ms.openlocfilehash: 553acc178bc5805b5afef5931fefc8ad74cbac39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135182"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="37599-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="37599-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="37599-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="37599-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37599-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37599-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="37599-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37599-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="37599-106">no O nome Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="37599-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="37599-107">[entrada, saída] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="37599-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="37599-108">Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32.</span><span class="sxs-lookup"><span data-stu-id="37599-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="37599-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.</span><span class="sxs-lookup"><span data-stu-id="37599-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="37599-110">fora Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="37599-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="37599-111">no O tamanho máximo do buffer apontado por `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37599-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="37599-112">fora O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37599-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37599-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="37599-113">Return Value</span></span>  
 <span data-ttu-id="37599-114">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="37599-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37599-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="37599-115">Remarks</span></span>  
 <span data-ttu-id="37599-116">Esse método é o mesmo que o método [ICLRStrongName:: GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="37599-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37599-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37599-117">Requirements</span></span>  
 <span data-ttu-id="37599-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37599-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37599-119">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="37599-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="37599-120">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37599-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37599-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37599-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37599-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37599-122">See also</span></span>

- [<span data-ttu-id="37599-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="37599-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="37599-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="37599-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
