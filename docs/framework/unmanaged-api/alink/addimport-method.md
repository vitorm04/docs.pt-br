---
title: Método AddImport
ms.date: 03/30/2017
api_name:
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aed70a78e2513f4d63fbf8ca8868f26efbac9ae8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787657"
---
# <a name="addimport-method"></a><span data-ttu-id="fa7a9-102">Método AddImport</span><span class="sxs-lookup"><span data-stu-id="fa7a9-102">AddImport Method</span></span>
<span data-ttu-id="fa7a9-103">Adiciona importações ao assembly.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa7a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa7a9-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa7a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa7a9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fa7a9-106">ID exclusiva do assembly a ser aumentada.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="fa7a9-107">ID exclusiva, recuperada do [Método ImportFile](importfile-method.md), do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-107">Unique ID, retrieved from [ImportFile Method](importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fa7a9-108">Sinalizadores de `ffContainsNoMetaData` FileDef com+, como `ffWriteable`e.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="fa7a9-109">`dwFlags`é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="fa7a9-109">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="fa7a9-110">Ponteiro para token que recebe a ID do arquivo resultante.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa7a9-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fa7a9-111">Return Value</span></span>  
 <span data-ttu-id="fa7a9-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="fa7a9-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa7a9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa7a9-113">Requirements</span></span>  
 <span data-ttu-id="fa7a9-114">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="fa7a9-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa7a9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa7a9-115">See also</span></span>

- [<span data-ttu-id="fa7a9-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="fa7a9-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="fa7a9-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="fa7a9-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="fa7a9-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="fa7a9-118">ALink API</span></span>](index.md)
