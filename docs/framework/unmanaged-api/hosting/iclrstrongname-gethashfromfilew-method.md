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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1547680800b188d5b5e0032e804c22cae0547ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771534"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="45341-102">Método ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="45341-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="45341-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="45341-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45341-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45341-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="45341-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45341-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="45341-106">[in] O nome do Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="45341-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="45341-107">[no, out] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="45341-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="45341-108">Algoritmos válidos são aquelas definidas por CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="45341-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="45341-109">Se `piHashAlg` é definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="45341-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="45341-110">[out] Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="45341-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="45341-111">[in] O tamanho máximo do buffer apontado por `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="45341-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="45341-112">[out] O tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="45341-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45341-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="45341-113">Return Value</span></span>  
 <span data-ttu-id="45341-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="45341-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45341-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="45341-115">Remarks</span></span>  
 <span data-ttu-id="45341-116">Esse método é igual a [iclrstrongname:: Gethashfromfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) , exceto que o nome do arquivo especificação é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="45341-116">This method is the same as the [ICLRStrongName::GetHashFromFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45341-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45341-117">Requirements</span></span>  
 <span data-ttu-id="45341-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45341-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45341-119">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="45341-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="45341-120">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="45341-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45341-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45341-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45341-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45341-122">See also</span></span>

- [<span data-ttu-id="45341-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="45341-123">GetHashFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="45341-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="45341-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
