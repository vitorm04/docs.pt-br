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
ms.openlocfilehash: d4b748370ff1aff042923002ad827a0e39d99963
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799270"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="6bcdb-102">Função GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="6bcdb-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="6bcdb-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="6bcdb-104">O caminho para o arquivo de assembly deve ser especificado como uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="6bcdb-105">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-105">This function has been deprecated.</span></span> <span data-ttu-id="6bcdb-106">Em vez disso, use o método [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6bcdb-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bcdb-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bcdb-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bcdb-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bcdb-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6bcdb-109">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="6bcdb-110">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6bcdb-111">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6bcdb-112">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6bcdb-113">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6bcdb-114">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6bcdb-115">fora O tamanho retornado, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6bcdb-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bcdb-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6bcdb-116">Requirements</span></span>  
 <span data-ttu-id="6bcdb-117">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bcdb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bcdb-118">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6bcdb-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6bcdb-119">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6bcdb-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bcdb-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bcdb-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bcdb-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bcdb-121">See also</span></span>

- [<span data-ttu-id="6bcdb-122">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="6bcdb-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="6bcdb-123">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="6bcdb-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="6bcdb-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6bcdb-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
