---
title: Método ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
ms.openlocfilehash: 8f6f2445d88d608d51be4e6fe1e064efbb58325d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763092"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="65829-102">Método ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="65829-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="65829-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="65829-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65829-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="65829-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65829-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="65829-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="65829-106">no O nome do contêiner de chave a ser excluído.</span><span class="sxs-lookup"><span data-stu-id="65829-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65829-107">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="65829-107">Return Value</span></span>  
 <span data-ttu-id="65829-108">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="65829-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65829-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="65829-109">Remarks</span></span>  
 <span data-ttu-id="65829-110">Use o método [ICLRStrongName:: StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) para importar um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="65829-110">Use the [ICLRStrongName::StrongNameKeyInstall](iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65829-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="65829-111">Requirements</span></span>  
 <span data-ttu-id="65829-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65829-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65829-113">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="65829-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="65829-114">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65829-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65829-115">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65829-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65829-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="65829-116">See also</span></span>

- [<span data-ttu-id="65829-117">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="65829-117">StrongNameKeyInstall Method</span></span>](iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="65829-118">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="65829-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
