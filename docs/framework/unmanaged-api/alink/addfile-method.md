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
ms.openlocfilehash: b1406c68f1f6abff4d140b131f5f630d0fd767e1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787692"
---
# <a name="addfile-method"></a><span data-ttu-id="1616e-102">Método AddFile</span><span class="sxs-lookup"><span data-stu-id="1616e-102">AddFile Method</span></span>
<span data-ttu-id="1616e-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="1616e-103">Adds files to the assembly.</span></span> <span data-ttu-id="1616e-104">Também pode ser usado para criar módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="1616e-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1616e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1616e-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1616e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1616e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1616e-107">ID exclusiva do assembly a ser aumentada.</span><span class="sxs-lookup"><span data-stu-id="1616e-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="1616e-108">Nome totalmente qualificado do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="1616e-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1616e-109">Sinalizadores de `ffContainsNoMetaData` FileDef com+, como `ffWriteable`e.</span><span class="sxs-lookup"><span data-stu-id="1616e-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="1616e-110">`dwFlags`é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="1616e-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="1616e-111">Interface de [interface IMetaDataEmit](../metadata/imetadataemit-interface.md) a ser usada para emitir metadados, se necessário.</span><span class="sxs-lookup"><span data-stu-id="1616e-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="1616e-112">Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.</span><span class="sxs-lookup"><span data-stu-id="1616e-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1616e-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1616e-113">Return Value</span></span>  
 <span data-ttu-id="1616e-114">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="1616e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1616e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1616e-115">Requirements</span></span>  
 <span data-ttu-id="1616e-116">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="1616e-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1616e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1616e-117">See also</span></span>

- [<span data-ttu-id="1616e-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="1616e-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="1616e-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="1616e-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="1616e-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="1616e-120">ALink API</span></span>](index.md)
