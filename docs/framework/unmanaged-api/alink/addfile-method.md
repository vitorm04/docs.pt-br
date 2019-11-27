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
ms.openlocfilehash: 4dd104805d547613315335bc9c95b5c60a9cab14
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446675"
---
# <a name="addfile-method"></a><span data-ttu-id="4cf00-102">Método AddFile</span><span class="sxs-lookup"><span data-stu-id="4cf00-102">AddFile Method</span></span>
<span data-ttu-id="4cf00-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="4cf00-103">Adds files to the assembly.</span></span> <span data-ttu-id="4cf00-104">Também pode ser usado para criar módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="4cf00-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cf00-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4cf00-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile(  
    mdAssembly      AssemblyID,  
    LPCWSTR         pszFilename,  
    DWORD           dwFlags,  
    IMetaDataEmit*  pEmitter,  
    mdFile*         pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cf00-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4cf00-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4cf00-107">ID exclusiva do assembly a ser aumentada.</span><span class="sxs-lookup"><span data-stu-id="4cf00-107">Unique ID of the assembly to be augmented.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="4cf00-108">Nome totalmente qualificado do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="4cf00-108">Fully qualified name of file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="4cf00-109">Sinalizadores de FileDef COM+, como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="4cf00-109">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="4cf00-110">`dwFlags` é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="4cf00-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="4cf00-111">Interface de [interface IMetaDataEmit](../metadata/imetadataemit-interface.md) a ser usada para emitir metadados, se necessário.</span><span class="sxs-lookup"><span data-stu-id="4cf00-111">[IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface to be used to emit metadata, if necessary.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="4cf00-112">Ponteiro para onde a ID exclusiva do arquivo adicionado será armazenada.</span><span class="sxs-lookup"><span data-stu-id="4cf00-112">Pointer to where the unique ID of the added file will be stored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cf00-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="4cf00-113">Return Value</span></span>  
 <span data-ttu-id="4cf00-114">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="4cf00-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4cf00-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4cf00-115">Requirements</span></span>  
 <span data-ttu-id="4cf00-116">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="4cf00-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf00-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4cf00-117">See also</span></span>

- [<span data-ttu-id="4cf00-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="4cf00-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4cf00-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="4cf00-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4cf00-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="4cf00-120">ALink API</span></span>](index.md)
