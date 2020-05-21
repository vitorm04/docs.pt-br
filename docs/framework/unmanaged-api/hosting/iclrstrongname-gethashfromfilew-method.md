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
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762091"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="033e4-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="033e4-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="033e4-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="033e4-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="033e4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="033e4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="033e4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="033e4-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="033e4-106">no O nome Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="033e4-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="033e4-107">[entrada, saída] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="033e4-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="033e4-108">Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32.</span><span class="sxs-lookup"><span data-stu-id="033e4-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="033e4-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.</span><span class="sxs-lookup"><span data-stu-id="033e4-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="033e4-110">fora Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="033e4-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="033e4-111">no O tamanho máximo do buffer apontado por `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="033e4-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="033e4-112">fora O tamanho, em bytes, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="033e4-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="033e4-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="033e4-113">Return Value</span></span>  
 <span data-ttu-id="033e4-114">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="033e4-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="033e4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="033e4-115">Remarks</span></span>  
 <span data-ttu-id="033e4-116">Esse método é o mesmo que o método [ICLRStrongName:: GetHashFromFile](iclrstrongname-gethashfromfile-method.md) , exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="033e4-116">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="033e4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="033e4-117">Requirements</span></span>  
 <span data-ttu-id="033e4-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="033e4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="033e4-119">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="033e4-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="033e4-120">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="033e4-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="033e4-121">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="033e4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="033e4-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="033e4-122">See also</span></span>

- [<span data-ttu-id="033e4-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="033e4-123">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="033e4-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="033e4-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
