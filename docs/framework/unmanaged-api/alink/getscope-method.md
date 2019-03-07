---
title: Método GetScope
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8de6c745b1d32c3d98f1b54e822ab084f0574b2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486193"
---
# <a name="getscope-method"></a><span data-ttu-id="f3334-102">Método GetScope</span><span class="sxs-lookup"><span data-stu-id="f3334-102">GetScope Method</span></span>
<span data-ttu-id="f3334-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="f3334-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3334-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f3334-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3334-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f3334-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f3334-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="f3334-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f3334-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="f3334-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f3334-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="f3334-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f3334-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="f3334-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3334-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f3334-110">Return Value</span></span>  
 <span data-ttu-id="f3334-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="f3334-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3334-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3334-112">Requirements</span></span>  
 <span data-ttu-id="f3334-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f3334-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3334-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3334-114">See also</span></span>
- [<span data-ttu-id="f3334-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f3334-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f3334-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f3334-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f3334-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f3334-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
