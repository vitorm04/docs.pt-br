---
title: Método ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
ms.openlocfilehash: 007de0365bf70b1f4a9a9e0f01807e7fdac19f54
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762143"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="7f800-102">Método ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="7f800-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="7f800-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="7f800-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f800-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f800-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f800-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f800-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="7f800-106">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="7f800-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="7f800-107">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="7f800-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="7f800-108">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="7f800-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="7f800-109">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="7f800-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="7f800-110">no O tamanho máximo solicitado de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="7f800-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="7f800-111">fora O tamanho retornado, em bytes, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="7f800-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f800-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="7f800-112">Return Value</span></span>  
 <span data-ttu-id="7f800-113">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="7f800-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f800-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f800-114">Requirements</span></span>  
 <span data-ttu-id="7f800-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f800-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f800-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="7f800-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7f800-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7f800-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f800-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f800-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f800-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="7f800-119">See also</span></span>

- [<span data-ttu-id="7f800-120">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="7f800-120">GetHashFromAssemblyFileW Method</span></span>](iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="7f800-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7f800-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
