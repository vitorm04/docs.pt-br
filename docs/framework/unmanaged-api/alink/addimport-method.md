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
ms.openlocfilehash: 31dec878c92e2e2196ab2d586a78578b7244a41a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742244"
---
# <a name="addimport-method"></a><span data-ttu-id="8076a-102">Método AddImport</span><span class="sxs-lookup"><span data-stu-id="8076a-102">AddImport Method</span></span>
<span data-ttu-id="8076a-103">Adiciona importações ao assembly.</span><span class="sxs-lookup"><span data-stu-id="8076a-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8076a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8076a-104">Syntax</span></span>  
  
```cpp  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8076a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8076a-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8076a-106">ID exclusiva do assembly a ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="8076a-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="8076a-107">ID exclusiva, recuperados do [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="8076a-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="8076a-108">Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="8076a-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="8076a-109">`dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="8076a-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="8076a-110">Ponteiro para o token que recebe a ID para o arquivo resultante.</span><span class="sxs-lookup"><span data-stu-id="8076a-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8076a-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8076a-111">Return Value</span></span>  
 <span data-ttu-id="8076a-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="8076a-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8076a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8076a-113">Requirements</span></span>  
 <span data-ttu-id="8076a-114">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="8076a-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8076a-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8076a-115">See also</span></span>

- [<span data-ttu-id="8076a-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8076a-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="8076a-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8076a-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="8076a-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8076a-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
