---
title: Método ImportTypes
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445684"
---
# <a name="importtypes-method"></a><span data-ttu-id="a89c7-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="a89c7-102">ImportTypes Method</span></span>
<span data-ttu-id="a89c7-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a89c7-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a89c7-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a89c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a89c7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a89c7-106">ID of the assembly to import to.</span><span class="sxs-lookup"><span data-stu-id="a89c7-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a89c7-107">ID of the file to import from.</span><span class="sxs-lookup"><span data-stu-id="a89c7-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="a89c7-108">Zero-based scope to import.</span><span class="sxs-lookup"><span data-stu-id="a89c7-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="a89c7-109">Receives enumerator handle for the types in this scope.</span><span class="sxs-lookup"><span data-stu-id="a89c7-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="a89c7-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a89c7-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="a89c7-111">Optionally receives count of types in the indicated scope.</span><span class="sxs-lookup"><span data-stu-id="a89c7-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a89c7-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a89c7-112">Return Value</span></span>  
 <span data-ttu-id="a89c7-113">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="a89c7-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a89c7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a89c7-114">Requirements</span></span>  
 <span data-ttu-id="a89c7-115">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="a89c7-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89c7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89c7-116">See also</span></span>

- [<span data-ttu-id="a89c7-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="a89c7-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a89c7-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="a89c7-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a89c7-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="a89c7-119">ALink API</span></span>](index.md)
