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
ms.openlocfilehash: 49dc456df684d6905370ee6ab8c8883449bea990
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498036"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="f8115-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="f8115-102">ExportNestedType Method</span></span>
<span data-ttu-id="f8115-103">Especifica os tipos aninhados como exportável.</span><span class="sxs-lookup"><span data-stu-id="f8115-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="f8115-104">O [método ExportType](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) também pode tipos aninhado de exportação, mas esse método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="f8115-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8115-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8115-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f8115-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8115-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f8115-107">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="f8115-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f8115-108">Token de arquivo ou Assembly de arquivo que define o tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="f8115-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="f8115-109">Tipo de token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="f8115-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="f8115-110">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="f8115-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f8115-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="f8115-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f8115-112">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f8115-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="f8115-113">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8115-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="f8115-114">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="f8115-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8115-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8115-115">Return Value</span></span>  
 <span data-ttu-id="f8115-116">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="f8115-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8115-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8115-117">Requirements</span></span>  
 <span data-ttu-id="f8115-118">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f8115-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8115-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8115-119">See also</span></span>
- [<span data-ttu-id="f8115-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f8115-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f8115-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f8115-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f8115-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f8115-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
