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
# <a name="exportnestedtype-method"></a><span data-ttu-id="18e64-102">Método ExportNestedType</span><span class="sxs-lookup"><span data-stu-id="18e64-102">ExportNestedType Method</span></span>
<span data-ttu-id="18e64-103">Especifica os tipos aninhados como exportáveis.</span><span class="sxs-lookup"><span data-stu-id="18e64-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="18e64-104">O [método ExportType](exporttype-method.md) também pode exportar tipos aninhados, mas esse método é mais rápido.</span><span class="sxs-lookup"><span data-stu-id="18e64-104">The [ExportType Method](exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18e64-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18e64-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="18e64-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18e64-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="18e64-107">ID do assembly do qual exportar.</span><span class="sxs-lookup"><span data-stu-id="18e64-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="18e64-108">Token de arquivo ou assembly de arquivo que define o tipo a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="18e64-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="18e64-109">Tipo de token do tipo a ser tornado exportável.</span><span class="sxs-lookup"><span data-stu-id="18e64-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="18e64-110">Token do tipo pai.</span><span class="sxs-lookup"><span data-stu-id="18e64-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="18e64-111">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="18e64-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="18e64-112">`ComType` sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="18e64-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="18e64-113">Esse valor pode ser passado para o [método DefineExportedType](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="18e64-113">This value may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="18e64-114">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="18e64-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18e64-115">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="18e64-115">Return Value</span></span>  
 <span data-ttu-id="18e64-116">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="18e64-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18e64-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="18e64-117">Requirements</span></span>  
 <span data-ttu-id="18e64-118">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="18e64-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e64-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18e64-119">See also</span></span>

- [<span data-ttu-id="18e64-120">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="18e64-120">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="18e64-121">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="18e64-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="18e64-122">API do ALink</span><span class="sxs-lookup"><span data-stu-id="18e64-122">ALink API</span></span>](index.md)
