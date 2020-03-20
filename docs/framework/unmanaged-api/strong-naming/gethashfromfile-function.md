---
title: Função GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176975"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="62a24-102">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="62a24-102">GetHashFromFile Function</span></span>
<span data-ttu-id="62a24-103">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="62a24-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="62a24-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="62a24-104">This function has been deprecated.</span></span> <span data-ttu-id="62a24-105">Use o método [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="62a24-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62a24-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62a24-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62a24-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="62a24-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="62a24-108">[em] O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="62a24-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="62a24-109">[dentro, fora] O algoritmo para usar ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="62a24-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="62a24-110">Algoritmos válidos são aqueles definidos pelo Win32 CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="62a24-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="62a24-111">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 é usado.</span><span class="sxs-lookup"><span data-stu-id="62a24-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="62a24-112">[fora] Uma matriz de byte contendo o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="62a24-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="62a24-113">[em] O tamanho máximo do `pbHash` buffer que aponta para.</span><span class="sxs-lookup"><span data-stu-id="62a24-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="62a24-114">[fora] O tamanho, em bytes, `pbHash`do devolvido.</span><span class="sxs-lookup"><span data-stu-id="62a24-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62a24-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="62a24-115">Remarks</span></span>  
 <span data-ttu-id="62a24-116">Esta função é a mesma [de GetHashFromFileW,](gethashfromfilew-function.md)exceto que a especificação do nome do arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="62a24-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62a24-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62a24-117">Requirements</span></span>  
 <span data-ttu-id="62a24-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62a24-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62a24-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="62a24-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="62a24-120">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62a24-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="62a24-121">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62a24-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a24-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="62a24-122">See also</span></span>

- [<span data-ttu-id="62a24-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="62a24-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="62a24-124">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="62a24-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="62a24-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="62a24-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
