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
ms.openlocfilehash: bbe8a43f44d59249abc713c95fce31f1fb9a5993
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148662"
---
# <a name="addimport-method"></a><span data-ttu-id="a37a7-102">Método AddImport</span><span class="sxs-lookup"><span data-stu-id="a37a7-102">AddImport Method</span></span>
<span data-ttu-id="a37a7-103">Adiciona importações ao assembly.</span><span class="sxs-lookup"><span data-stu-id="a37a7-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a37a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a37a7-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a37a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a37a7-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a37a7-106">ID exclusiva do assembly a ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="a37a7-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="a37a7-107">ID exclusiva, recuperados do [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), do arquivo a ser importado.</span><span class="sxs-lookup"><span data-stu-id="a37a7-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a37a7-108">Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="a37a7-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="a37a7-109">`dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a37a7-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="a37a7-110">Ponteiro para o token que recebe a ID para o arquivo resultante.</span><span class="sxs-lookup"><span data-stu-id="a37a7-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a37a7-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a37a7-111">Return Value</span></span>  
 <span data-ttu-id="a37a7-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="a37a7-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a37a7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a37a7-113">Requirements</span></span>  
 <span data-ttu-id="a37a7-114">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="a37a7-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a37a7-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a37a7-115">See also</span></span>

- [<span data-ttu-id="a37a7-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="a37a7-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a37a7-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="a37a7-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a37a7-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="a37a7-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
