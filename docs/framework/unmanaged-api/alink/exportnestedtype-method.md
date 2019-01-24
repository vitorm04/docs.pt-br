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
ms.openlocfilehash: 5c7ea671af5c6c725df136810bb8cf6610a6f83f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710333"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="c4fdd-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="c4fdd-102">ExportNestedType Method</span></span>
<span data-ttu-id="c4fdd-103">Especifica os tipos aninhados como exportável.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="c4fdd-104">O [método ExportType](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) também pode tipos aninhado de exportação, mas esse método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4fdd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4fdd-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c4fdd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4fdd-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c4fdd-107">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c4fdd-108">Token de arquivo ou Assembly de arquivo que define o tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="c4fdd-109">Tipo de token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="c4fdd-110">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="c4fdd-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="c4fdd-112">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="c4fdd-113">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="c4fdd-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="c4fdd-114">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4fdd-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c4fdd-115">Return Value</span></span>  
 <span data-ttu-id="c4fdd-116">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="c4fdd-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4fdd-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c4fdd-117">Requirements</span></span>  
 <span data-ttu-id="c4fdd-118">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="c4fdd-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4fdd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4fdd-119">See also</span></span>
- [<span data-ttu-id="c4fdd-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="c4fdd-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="c4fdd-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="c4fdd-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="c4fdd-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="c4fdd-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
