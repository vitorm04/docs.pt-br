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
ms.openlocfilehash: c5798fc488cf4453b6abcf00a7169b1ec0b529ec
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965365"
---
# <a name="getscope-method"></a><span data-ttu-id="c0147-102">Método GetScope</span><span class="sxs-lookup"><span data-stu-id="c0147-102">GetScope Method</span></span>
<span data-ttu-id="c0147-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="c0147-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0147-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c0147-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0147-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c0147-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c0147-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="c0147-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c0147-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="c0147-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c0147-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="c0147-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c0147-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="c0147-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0147-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c0147-110">Return Value</span></span>  
 <span data-ttu-id="c0147-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c0147-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0147-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c0147-112">Requirements</span></span>  
 <span data-ttu-id="c0147-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c0147-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0147-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0147-114">See also</span></span>
- [<span data-ttu-id="c0147-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c0147-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c0147-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c0147-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c0147-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c0147-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
