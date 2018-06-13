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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0afe4daa1c85f3e15addac55bdbe631d40e03f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407548"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="e2471-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="e2471-102">ExportNestedType Method</span></span>
<span data-ttu-id="e2471-103">Especifica tipos aninhados como exportável.</span><span class="sxs-lookup"><span data-stu-id="e2471-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="e2471-104">O [método ExportType](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) também pode criar tipos de exportação aninhado, mas esse método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="e2471-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2471-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e2471-105">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="e2471-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e2471-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e2471-107">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="e2471-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e2471-108">Token de arquivo ou Assembly de arquivo que define o tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="e2471-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="e2471-109">Tipo de token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="e2471-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="e2471-110">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="e2471-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e2471-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="e2471-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e2471-112">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="e2471-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e2471-113">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="e2471-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e2471-114">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="e2471-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2471-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e2471-115">Return Value</span></span>  
 <span data-ttu-id="e2471-116">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="e2471-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2471-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e2471-117">Requirements</span></span>  
 <span data-ttu-id="e2471-118">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="e2471-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2471-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2471-119">See Also</span></span>  
 [<span data-ttu-id="e2471-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="e2471-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e2471-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="e2471-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e2471-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="e2471-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
