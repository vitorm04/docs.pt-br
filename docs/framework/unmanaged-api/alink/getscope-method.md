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
ms.openlocfilehash: f3c3142ca12789b086bcd8b5a9c00c943264ae7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741849"
---
# <a name="getscope-method"></a><span data-ttu-id="425a0-102">Método GetScope</span><span class="sxs-lookup"><span data-stu-id="425a0-102">GetScope Method</span></span>
<span data-ttu-id="425a0-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="425a0-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="425a0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="425a0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="425a0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="425a0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="425a0-106">ID exclusiva do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="425a0-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="425a0-107">ID exclusiva do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="425a0-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="425a0-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="425a0-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="425a0-109">Recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para o escopo.</span><span class="sxs-lookup"><span data-stu-id="425a0-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="425a0-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="425a0-110">Return Value</span></span>  
 <span data-ttu-id="425a0-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="425a0-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="425a0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="425a0-112">Requirements</span></span>  
 <span data-ttu-id="425a0-113">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="425a0-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="425a0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="425a0-114">See also</span></span>

- [<span data-ttu-id="425a0-115">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="425a0-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="425a0-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="425a0-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="425a0-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="425a0-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
