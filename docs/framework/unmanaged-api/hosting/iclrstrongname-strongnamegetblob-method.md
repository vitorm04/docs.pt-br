---
title: Método ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: f93d3f0322de89b2e9ce596329c06b58db9fdcdc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760297"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="62076-102">Método ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="62076-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="62076-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="62076-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62076-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="62076-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62076-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="62076-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="62076-106">no Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="62076-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="62076-107">no O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="62076-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="62076-108">[entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="62076-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="62076-109">No retorno, o tamanho real, em bytes, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="62076-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62076-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="62076-110">Return Value</span></span>  
 <span data-ttu-id="62076-111">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="62076-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62076-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="62076-112">Requirements</span></span>  
 <span data-ttu-id="62076-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62076-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62076-114">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="62076-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="62076-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="62076-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62076-116">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62076-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62076-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="62076-117">See also</span></span>

- [<span data-ttu-id="62076-118">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="62076-118">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="62076-119">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="62076-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
