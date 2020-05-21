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
ms.openlocfilehash: edce771b3c36f2c56637aa2a21fe524be0ae12c8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763014"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="6b86b-102">Método ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="6b86b-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="6b86b-103">Retorna o tamanho da assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="6b86b-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="6b86b-104">Esse método é normalmente usado por compiladores para determinar a quantidade de espaço a ser reservada no arquivo ao criar um assembly com assinatura atrasada.</span><span class="sxs-lookup"><span data-stu-id="6b86b-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b86b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b86b-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="6b86b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b86b-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="6b86b-107">no Uma estrutura do tipo [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="6b86b-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="6b86b-108">no O tamanho, em bytes, de `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="6b86b-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="6b86b-109">no O número de bytes necessários para armazenar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="6b86b-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b86b-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="6b86b-110">Return Value</span></span>  
 <span data-ttu-id="6b86b-111">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="6b86b-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b86b-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b86b-112">Requirements</span></span>  
 <span data-ttu-id="6b86b-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b86b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b86b-114">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="6b86b-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6b86b-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b86b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b86b-116">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b86b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b86b-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="6b86b-117">See also</span></span>

- [<span data-ttu-id="6b86b-118">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6b86b-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
