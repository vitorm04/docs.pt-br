---
title: Método1 AddImport
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
ms.openlocfilehash: d2daed0450e04137621788e830bbedb467bd57c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706333"
---
# <a name="addimport-method1"></a><span data-ttu-id="553d9-102">Método1 AddImport</span><span class="sxs-lookup"><span data-stu-id="553d9-102">AddImport Method1</span></span>
<span data-ttu-id="553d9-103">Adiciona importações ao assembly.</span><span class="sxs-lookup"><span data-stu-id="553d9-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="553d9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="553d9-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="553d9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="553d9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="553d9-106">ID exclusiva do assembly a ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="553d9-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="553d9-107">ID exclusiva, recuperados do [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="553d9-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="553d9-108">Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="553d9-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="553d9-109">`dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="553d9-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="553d9-110">Ponteiro para o token que recebe a ID para o arquivo resultante.</span><span class="sxs-lookup"><span data-stu-id="553d9-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="553d9-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="553d9-111">Return Value</span></span>  
 <span data-ttu-id="553d9-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="553d9-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="553d9-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="553d9-113">Requirements</span></span>  
 <span data-ttu-id="553d9-114">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="553d9-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553d9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="553d9-115">See also</span></span>
- [<span data-ttu-id="553d9-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="553d9-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="553d9-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="553d9-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="553d9-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="553d9-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
