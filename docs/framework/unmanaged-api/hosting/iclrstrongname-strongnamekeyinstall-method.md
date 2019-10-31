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
ms.openlocfilehash: 693a5831934647256ac48c8f3a2d30325dee4349
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135031"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="ed737-102">Método ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="ed737-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="ed737-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="ed737-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed737-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ed737-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed737-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ed737-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ed737-106">no O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="ed737-106">[in] The name of the key container.</span></span> <span data-ttu-id="ed737-107">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="ed737-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ed737-108">no O par de chaves binárias.</span><span class="sxs-lookup"><span data-stu-id="ed737-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ed737-109">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ed737-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed737-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ed737-110">Return Value</span></span>  
 <span data-ttu-id="ed737-111">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="ed737-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed737-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="ed737-112">Remarks</span></span>  
 <span data-ttu-id="ed737-113">Use o método [ICLRStrongName:: StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="ed737-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed737-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ed737-114">Requirements</span></span>  
 <span data-ttu-id="ed737-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed737-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed737-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ed737-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ed737-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ed737-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed737-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed737-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed737-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed737-119">See also</span></span>

- [<span data-ttu-id="ed737-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="ed737-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="ed737-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ed737-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
