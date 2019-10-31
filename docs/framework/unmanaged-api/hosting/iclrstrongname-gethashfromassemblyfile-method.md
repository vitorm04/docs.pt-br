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
ms.openlocfilehash: 3fd9efd3961be1d6e6e91b881327628c598e364e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092718"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="53b26-102">Método ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="53b26-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="53b26-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="53b26-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53b26-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="53b26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53b26-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="53b26-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="53b26-106">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="53b26-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="53b26-107">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="53b26-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="53b26-108">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="53b26-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="53b26-109">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="53b26-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="53b26-110">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="53b26-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="53b26-111">fora O tamanho retornado, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="53b26-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53b26-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="53b26-112">Return Value</span></span>  
 <span data-ttu-id="53b26-113">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="53b26-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53b26-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53b26-114">Requirements</span></span>  
 <span data-ttu-id="53b26-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53b26-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53b26-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="53b26-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="53b26-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="53b26-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53b26-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53b26-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b26-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53b26-119">See also</span></span>

- [<span data-ttu-id="53b26-120">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="53b26-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="53b26-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="53b26-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
