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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d60e1e503cd48b9b9e2ed91a6bfea000aeeea2af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527870"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="db148-102">Método ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="db148-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="db148-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="db148-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db148-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db148-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db148-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db148-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="db148-106">[in] O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="db148-106">[in] The name of the key container.</span></span> <span data-ttu-id="db148-107">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="db148-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="db148-108">[in] O par de chaves binário.</span><span class="sxs-lookup"><span data-stu-id="db148-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="db148-109">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="db148-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db148-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="db148-110">Return Value</span></span>  
 <span data-ttu-id="db148-111">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="db148-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db148-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="db148-112">Remarks</span></span>  
 <span data-ttu-id="db148-113">Use o [iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="db148-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db148-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db148-114">Requirements</span></span>  
 <span data-ttu-id="db148-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db148-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db148-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="db148-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="db148-117">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="db148-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="db148-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db148-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db148-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db148-119">See Also</span></span>  
 [<span data-ttu-id="db148-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="db148-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="db148-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="db148-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
