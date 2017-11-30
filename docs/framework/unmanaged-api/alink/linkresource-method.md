---
title: "Método LinkResource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.LinkResource
api_location: alink.dll
api_type: COM
f1_keywords: LinkResource
helpviewer_keywords: LinkResource method
ms.assetid: c404acb3-4c59-4100-9a4c-483cbdb1d736
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8cb1f985c1d735fa20507ab90d478e97025c9e2c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-method"></a><span data-ttu-id="bfde5-102">Método LinkResource</span><span class="sxs-lookup"><span data-stu-id="bfde5-102">LinkResource Method</span></span>
<span data-ttu-id="bfde5-103">Links em um recurso.</span><span class="sxs-lookup"><span data-stu-id="bfde5-103">Links in a resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfde5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfde5-104">Syntax</span></span>  
  
```  
HRESULT LinkResource(  
    mdAssembly  AssemblyID,  
    LPCWSTR     pszFileName,  
    LPCWSTR     pszNewLocation,  
    LPCWSTR     pszResourceName,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfde5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bfde5-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="bfde5-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="bfde5-106">ID of the assembly.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="bfde5-107">Nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="bfde5-107">Name of the file.</span></span>  
  
 `pszNewLocation`  
 <span data-ttu-id="bfde5-108">Nome de arquivo novo opcional.</span><span class="sxs-lookup"><span data-stu-id="bfde5-108">Optional new file name.</span></span> <span data-ttu-id="bfde5-109">Se não nulo, `pszFileName` pszNewLocation serão copiados.</span><span class="sxs-lookup"><span data-stu-id="bfde5-109">If non-NULL, `pszFileName` will be copied to pszNewLocation.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="bfde5-110">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="bfde5-110">Name of the resource.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="bfde5-111">Acessibilidade como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="bfde5-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="bfde5-112">Esse parâmetro pode ser passado para [método DefineManifestResource](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span><span class="sxs-lookup"><span data-stu-id="bfde5-112">This parameter may be passed to [DefineManifestResource Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definemanifestresource-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfde5-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bfde5-113">Return Value</span></span>  
 <span data-ttu-id="bfde5-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="bfde5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfde5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bfde5-115">Requirements</span></span>  
 <span data-ttu-id="bfde5-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="bfde5-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfde5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfde5-117">See Also</span></span>  
 [<span data-ttu-id="bfde5-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="bfde5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="bfde5-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="bfde5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="bfde5-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="bfde5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
