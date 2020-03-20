---
title: Método ICLRStrongName::StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176338"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="63a6f-102">Método ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="63a6f-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="63a6f-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="63a6f-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="63a6f-104">Este método é normalmente usado por compiladores para determinar quanto espaço reservar no arquivo ao criar um conjunto assinado por atraso.</span><span class="sxs-lookup"><span data-stu-id="63a6f-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a6f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63a6f-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="63a6f-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="63a6f-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="63a6f-107">[em] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usada para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="63a6f-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="63a6f-108">[em] O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="63a6f-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="63a6f-109">[em] O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="63a6f-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63a6f-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="63a6f-110">Return Value</span></span>  
 <span data-ttu-id="63a6f-111">`S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="63a6f-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63a6f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63a6f-112">Requirements</span></span>  
 <span data-ttu-id="63a6f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63a6f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a6f-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="63a6f-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="63a6f-115">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63a6f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63a6f-116">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a6f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a6f-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="63a6f-117">See also</span></span>

- [<span data-ttu-id="63a6f-118">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="63a6f-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
