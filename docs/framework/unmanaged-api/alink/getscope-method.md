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
ms.openlocfilehash: 571612796d4e66be9dd8469d748c2380c839ddfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789812"
---
# <a name="getscope-method"></a><span data-ttu-id="e60ea-102">Método GetScope</span><span class="sxs-lookup"><span data-stu-id="e60ea-102">GetScope Method</span></span>
<span data-ttu-id="e60ea-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="e60ea-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e60ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e60ea-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e60ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e60ea-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e60ea-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="e60ea-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e60ea-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="e60ea-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="e60ea-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="e60ea-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="e60ea-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="e60ea-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e60ea-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e60ea-110">Return Value</span></span>  
 <span data-ttu-id="e60ea-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="e60ea-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e60ea-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e60ea-112">Requirements</span></span>  
 <span data-ttu-id="e60ea-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="e60ea-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e60ea-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e60ea-114">See also</span></span>

- [<span data-ttu-id="e60ea-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="e60ea-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="e60ea-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="e60ea-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="e60ea-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="e60ea-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
