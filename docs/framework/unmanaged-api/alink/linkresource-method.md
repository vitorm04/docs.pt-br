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
ms.openlocfilehash: 6e851c1bd56c0e9ece02fb06c0dcd9975a5b02ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949091"
---
# <a name="linkresource-method"></a><span data-ttu-id="c795e-102">Método LinkResource</span><span class="sxs-lookup"><span data-stu-id="c795e-102">LinkResource Method</span></span>
<span data-ttu-id="c795e-103">Links em um recurso.</span><span class="sxs-lookup"><span data-stu-id="c795e-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c795e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c795e-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c795e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c795e-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c795e-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="c795e-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="c795e-107">Nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c795e-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="c795e-108">Nome do arquivo novo opcional.</span><span class="sxs-lookup"><span data-stu-id="c795e-108">Optional new file name.</span></span> <span data-ttu-id="c795e-109">Se não for nulo, `pszFileName` pszNewLocation serão copiados.</span><span class="sxs-lookup"><span data-stu-id="c795e-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="c795e-110">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="c795e-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c795e-111">Acessibilidade, como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="c795e-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="c795e-112">Esse parâmetro pode ser passado para [método DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="c795e-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c795e-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c795e-113">Return Value</span></span>  
 <span data-ttu-id="c795e-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c795e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c795e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c795e-115">Requirements</span></span>  
 <span data-ttu-id="c795e-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="c795e-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c795e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c795e-117">See also</span></span>

- [<span data-ttu-id="c795e-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c795e-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c795e-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c795e-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c795e-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c795e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
