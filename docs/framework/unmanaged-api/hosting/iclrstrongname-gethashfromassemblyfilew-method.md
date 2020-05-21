---
title: Método ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: f44753b3e836b43bc09548a35eb68f0f22e3170f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762130"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="56aed-102">Método ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="56aed-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="56aed-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="56aed-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56aed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56aed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56aed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56aed-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="56aed-106">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="56aed-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="56aed-107">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="56aed-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="56aed-108">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="56aed-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="56aed-109">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="56aed-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="56aed-110">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="56aed-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="56aed-111">no O tamanho máximo solicitado de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="56aed-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="56aed-112">fora O tamanho retornado, em bytes, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="56aed-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56aed-113">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="56aed-113">Return Value</span></span>  
 <span data-ttu-id="56aed-114">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="56aed-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56aed-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56aed-115">Requirements</span></span>  
 <span data-ttu-id="56aed-116">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56aed-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56aed-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="56aed-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="56aed-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56aed-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56aed-119">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56aed-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56aed-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="56aed-120">See also</span></span>

- [<span data-ttu-id="56aed-121">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="56aed-121">GetHashFromAssemblyFile Method</span></span>](iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="56aed-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="56aed-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
