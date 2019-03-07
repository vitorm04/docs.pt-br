---
title: Método LinkResource
ms.date: 03/30/2017
api_name:
- IALink.LinkResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- LinkResource
helpviewer_keywords:
- LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 61f82a34c287c62e1180c9c6bbe090914763afa3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479074"
---
# <a name="linkresource-method"></a><span data-ttu-id="f9990-102">Método LinkResource</span><span class="sxs-lookup"><span data-stu-id="f9990-102">LinkResource Method</span></span>
<span data-ttu-id="f9990-103">Links em um recurso.</span><span class="sxs-lookup"><span data-stu-id="f9990-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9990-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9990-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9990-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9990-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f9990-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f9990-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="f9990-107">Nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="f9990-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="f9990-108">Nome do arquivo novo opcional.</span><span class="sxs-lookup"><span data-stu-id="f9990-108">Optional new file name.</span></span> <span data-ttu-id="f9990-109">Se não for nulo, `pszFileName` pszNewLocation serão copiados.</span><span class="sxs-lookup"><span data-stu-id="f9990-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="f9990-110">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="f9990-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f9990-111">Acessibilidade, como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="f9990-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="f9990-112">Esse parâmetro pode ser passado para [método DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="f9990-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f9990-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f9990-113">Return Value</span></span>  
 <span data-ttu-id="f9990-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="f9990-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9990-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9990-115">Requirements</span></span>  
 <span data-ttu-id="f9990-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="f9990-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9990-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9990-117">See also</span></span>
- [<span data-ttu-id="f9990-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f9990-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f9990-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f9990-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f9990-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f9990-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
