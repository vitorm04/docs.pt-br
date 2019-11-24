---
title: Método EmbedResource
ms.date: 03/30/2017
api_name:
- IALink.EmbedResource
- EmbedResource
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmbedResource
helpviewer_keywords:
- EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type:
- apiref
ms.openlocfilehash: 24279870e7406de649df56e8aad31252513e95c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446544"
---
# <a name="embedresource-method"></a><span data-ttu-id="8d9a8-102">Método EmbedResource</span><span class="sxs-lookup"><span data-stu-id="8d9a8-102">EmbedResource Method</span></span>
<span data-ttu-id="8d9a8-103">Declares an embedded resource.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-103">Declares an embedded resource.</span></span> <span data-ttu-id="8d9a8-104">This method does not actually embed the resource.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d9a8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d9a8-105">Syntax</span></span>  
  
```cpp  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d9a8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8d9a8-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8d9a8-107">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8d9a8-108">File token or assembly ID of file that contains the resource.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="8d9a8-109">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="8d9a8-110">Offset of resource from RVA.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8d9a8-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="8d9a8-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d9a8-112">These flags may be passed to [DefineExportedType Method](../metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d9a8-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8d9a8-113">Return Value</span></span>  
 <span data-ttu-id="8d9a8-114">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d9a8-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8d9a8-115">Requirements</span></span>  
 <span data-ttu-id="8d9a8-116">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="8d9a8-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d9a8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d9a8-117">See also</span></span>

- [<span data-ttu-id="8d9a8-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8d9a8-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8d9a8-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8d9a8-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8d9a8-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8d9a8-120">ALink API</span></span>](index.md)
