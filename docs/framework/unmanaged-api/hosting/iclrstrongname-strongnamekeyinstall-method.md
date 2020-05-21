---
title: Método ICLRStrongName::StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
ms.openlocfilehash: e0c60d6e74c48531a223f6dbb35125b5a2017cbb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763030"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="9e29b-102">Método ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="9e29b-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="9e29b-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="9e29b-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e29b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e29b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e29b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e29b-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="9e29b-106">no O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="9e29b-106">[in] The name of the key container.</span></span> <span data-ttu-id="9e29b-107">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="9e29b-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9e29b-108">no O par de chaves binárias.</span><span class="sxs-lookup"><span data-stu-id="9e29b-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9e29b-109">no O tamanho, em bytes, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="9e29b-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e29b-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="9e29b-110">Return Value</span></span>  
 <span data-ttu-id="9e29b-111">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="9e29b-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e29b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e29b-112">Remarks</span></span>  
 <span data-ttu-id="9e29b-113">Use o método [ICLRStrongName:: StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="9e29b-113">Use the [ICLRStrongName::StrongNameKeyDelete](iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e29b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e29b-114">Requirements</span></span>  
 <span data-ttu-id="9e29b-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e29b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e29b-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="9e29b-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9e29b-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e29b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e29b-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e29b-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="9e29b-119">See also</span></span>

- [<span data-ttu-id="9e29b-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="9e29b-120">StrongNameKeyDelete Method</span></span>](iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="9e29b-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9e29b-121">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
