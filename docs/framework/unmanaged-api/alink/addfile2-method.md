---
title: Método AddFile2
ms.date: 03/30/2017
api_name:
- AddFile2
- IALink2.AddFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddFile2
helpviewer_keywords:
- AddFile2 method
ms.assetid: 03bc49bf-a89b-4fb6-a88d-97482e061195
topic_type:
- apiref
ms.openlocfilehash: 8dadf9ec8f896b03e4918b21f5153c1b747010fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446669"
---
# <a name="addfile2-method"></a><span data-ttu-id="a2e80-102">Método AddFile2</span><span class="sxs-lookup"><span data-stu-id="a2e80-102">AddFile2 Method</span></span>
<span data-ttu-id="a2e80-103">Adiciona arquivos ao assembly.</span><span class="sxs-lookup"><span data-stu-id="a2e80-103">Adds files to the assembly.</span></span> <span data-ttu-id="a2e80-104">Também pode ser usado para criar módulos desvinculados.</span><span class="sxs-lookup"><span data-stu-id="a2e80-104">Can also be used to create unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2e80-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2e80-105">Syntax</span></span>  
  
```cpp  
HRESULT AddFile2(  
    mdAssembly AssemblyID,  
    LPCWSTR pszFilename,  
    DWORD dwFlags,  
    IMetaDataEmit2* pEmitter,  
    mdFile* pFileToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2e80-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a2e80-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a2e80-107">ID do assembly ao qual o arquivo é adicionado.</span><span class="sxs-lookup"><span data-stu-id="a2e80-107">ID for the assembly to which the file is added.</span></span>  
  
 `pszFilename`  
 <span data-ttu-id="a2e80-108">Nome do arquivo a ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="a2e80-108">Name of the file to be added.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a2e80-109">Sinalizadores de `FileDef` COM+, como `ffContainsNoMetaData` e `ffWriteable`.</span><span class="sxs-lookup"><span data-stu-id="a2e80-109">COM+ `FileDef` flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="a2e80-110">`dwFlags` é passado para o [método definofile](../metadata/imetadataassemblyemit-definefile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2e80-110">`dwFlags` is passed to [DefineFile Method](../metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="a2e80-111">Interface para interface de [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a2e80-111">Interface to [IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface.</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="a2e80-112">Recebe a ID do arquivo que está sendo adicionado.</span><span class="sxs-lookup"><span data-stu-id="a2e80-112">Receives ID for the file being added.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2e80-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a2e80-113">Return Value</span></span>  
 <span data-ttu-id="a2e80-114">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="a2e80-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2e80-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a2e80-115">Requirements</span></span>  
 <span data-ttu-id="a2e80-116">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="a2e80-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2e80-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2e80-117">See also</span></span>

- [<span data-ttu-id="a2e80-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="a2e80-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a2e80-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="a2e80-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a2e80-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="a2e80-120">ALink API</span></span>](index.md)
