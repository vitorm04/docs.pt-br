---
title: Método ExportNestedType
ms.date: 03/30/2017
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportNestedType
helpviewer_keywords:
- ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type:
- apiref
ms.openlocfilehash: fded6b95144d4088a2abc8dfcc4ef8eda331c34f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438427"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="21830-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="21830-102">ExportNestedType Method</span></span>
<span data-ttu-id="21830-103">Specifies nested types as exportable.</span><span class="sxs-lookup"><span data-stu-id="21830-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="21830-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span><span class="sxs-lookup"><span data-stu-id="21830-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21830-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21830-105">Syntax</span></span>  
  
```cpp  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="21830-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21830-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="21830-107">ID of assembly to export from.</span><span class="sxs-lookup"><span data-stu-id="21830-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="21830-108">File token or Assembly of file that defines the type to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="21830-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="21830-109">Type token of type to be made exportable.</span><span class="sxs-lookup"><span data-stu-id="21830-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="21830-110">Token of parent type.</span><span class="sxs-lookup"><span data-stu-id="21830-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="21830-111">Fully qualified type name to export.</span><span class="sxs-lookup"><span data-stu-id="21830-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="21830-112">`ComType` flags such as `tdPublic` or `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="21830-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="21830-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="21830-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="21830-114">Receives token for exported type.</span><span class="sxs-lookup"><span data-stu-id="21830-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21830-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="21830-115">Return Value</span></span>  
 <span data-ttu-id="21830-116">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="21830-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21830-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21830-117">Requirements</span></span>  
 <span data-ttu-id="21830-118">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="21830-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21830-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21830-119">See also</span></span>

- [<span data-ttu-id="21830-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="21830-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21830-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="21830-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21830-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="21830-122">ALink API</span></span>](index.md)
