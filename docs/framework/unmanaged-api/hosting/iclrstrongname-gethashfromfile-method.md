---
title: Método ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: 798bb0585bfe4cc29afba2fbefae818301704613
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135187"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="c36f2-102">Método ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="c36f2-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="c36f2-103">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="c36f2-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c36f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c36f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c36f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c36f2-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="c36f2-106">no O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="c36f2-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c36f2-107">[entrada, saída] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="c36f2-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="c36f2-108">Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32.</span><span class="sxs-lookup"><span data-stu-id="c36f2-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="c36f2-109">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.</span><span class="sxs-lookup"><span data-stu-id="c36f2-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c36f2-110">fora Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="c36f2-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c36f2-111">no O tamanho máximo do buffer ao qual `pbHash` aponta.</span><span class="sxs-lookup"><span data-stu-id="c36f2-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c36f2-112">fora O tamanho, em bytes, do `pbHash`retornado.</span><span class="sxs-lookup"><span data-stu-id="c36f2-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c36f2-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c36f2-113">Return Value</span></span>  
 <span data-ttu-id="c36f2-114">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="c36f2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c36f2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c36f2-115">Remarks</span></span>  
 <span data-ttu-id="c36f2-116">Esse método é o mesmo que o método [ICLRStrongName:: GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) , exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="c36f2-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c36f2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c36f2-117">Requirements</span></span>  
 <span data-ttu-id="c36f2-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c36f2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c36f2-119">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c36f2-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c36f2-120">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c36f2-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c36f2-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c36f2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c36f2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c36f2-122">See also</span></span>

- [<span data-ttu-id="c36f2-123">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="c36f2-123">GetHashFromFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="c36f2-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c36f2-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
