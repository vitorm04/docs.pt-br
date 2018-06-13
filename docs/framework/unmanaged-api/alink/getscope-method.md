---
title: GetScope Method1
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
ms.openlocfilehash: e2746073fbc6adfd7090aa9b3cc38e46c4411744
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400179"
---
# <a name="getscope-method1"></a><span data-ttu-id="6c265-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="6c265-102">GetScope Method1</span></span>
<span data-ttu-id="6c265-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="6c265-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c265-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c265-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c265-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6c265-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6c265-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="6c265-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6c265-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="6c265-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="6c265-108">Escopo com base em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="6c265-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="6c265-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="6c265-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c265-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6c265-110">Return Value</span></span>  
 <span data-ttu-id="6c265-111">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="6c265-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c265-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6c265-112">Requirements</span></span>  
 <span data-ttu-id="6c265-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="6c265-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c265-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c265-114">See Also</span></span>  
 [<span data-ttu-id="6c265-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="6c265-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6c265-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="6c265-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6c265-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="6c265-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
