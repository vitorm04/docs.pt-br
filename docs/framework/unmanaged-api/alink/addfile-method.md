---
title: Método AddFile
ms.date: 03/30/2017
api_name:
- IALink.AddFile
- AddFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile
helpviewer_keywords:
- AddFile method
ms.assetid: 9e707abb-f905-4568-9356-12aa21d1b11c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 056d1ac0ffd3ad7fa7cb1f86ae13331ac38b3eff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162202"
---
# <a name="addfile-method"></a><span data-ttu-id="ca138-102">Método AddFile</span><span class="sxs-lookup"><span data-stu-id="ca138-102">AddFile Method</span></span>
<span data-ttu-id="ca138-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="ca138-103">Adds files to the assembly.</span></span> <span data-ttu-id="ca138-104">Também pode ser usado para criar os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="ca138-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca138-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca138-105">Syntax</span></span>  
  
```  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca138-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca138-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ca138-107">ID exclusiva do assembly a ser aumentado.</span><span class="sxs-lookup"><span data-stu-id="ca138-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="ca138-108">Nome totalmente qualificado do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="ca138-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ca138-109">Como sinalizadores de COM+ FileDef `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="ca138-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="ca138-110">`dwFlags` é passado para [método DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="ca138-110">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="ca138-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface a ser usado para emitir metadados, se necessário.</span><span class="sxs-lookup"><span data-stu-id="ca138-111">[IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="ca138-112">Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.</span><span class="sxs-lookup"><span data-stu-id="ca138-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca138-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ca138-113">Return Value</span></span>  
 <span data-ttu-id="ca138-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="ca138-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca138-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca138-115">Requirements</span></span>  
 <span data-ttu-id="ca138-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="ca138-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca138-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ca138-117">See also</span></span>

- [<span data-ttu-id="ca138-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ca138-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="ca138-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ca138-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="ca138-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ca138-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
