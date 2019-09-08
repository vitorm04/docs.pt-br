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
ms.openlocfilehash: 570e48788a11045882ef546bf6bc22315c2a02b0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777269"
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="52bae-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="52bae-102">ExportNestedType Method</span></span>
<span data-ttu-id="52bae-103">Especifica os tipos aninhados como exportáveis.</span><span class="sxs-lookup"><span data-stu-id="52bae-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="52bae-104">O [método ExportType](exporttype-method.md) também pode exportar tipos aninhados, mas esse método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="52bae-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52bae-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52bae-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="52bae-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52bae-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="52bae-107">ID do assembly do qual exportar.</span><span class="sxs-lookup"><span data-stu-id="52bae-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="52bae-108">Token de arquivo ou assembly de arquivo que define o tipo a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="52bae-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="52bae-109">Tipo de token do tipo a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="52bae-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="52bae-110">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="52bae-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="52bae-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="52bae-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="52bae-112">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="52bae-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="52bae-113">Esse valor pode ser passado para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="52bae-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="52bae-114">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="52bae-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52bae-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="52bae-115">Return Value</span></span>  
 <span data-ttu-id="52bae-116">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="52bae-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52bae-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52bae-117">Requirements</span></span>  
 <span data-ttu-id="52bae-118">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="52bae-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52bae-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52bae-119">See also</span></span>

- [<span data-ttu-id="52bae-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="52bae-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="52bae-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="52bae-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="52bae-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="52bae-122">ALink API</span></span>](index.md)
