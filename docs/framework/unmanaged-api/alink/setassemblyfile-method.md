---
title: Método SetAssemblyFile
ms.date: 03/30/2017
api_name:
- IALink.SetAssemblyFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile
helpviewer_keywords:
- SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 76d341aca7c96e5932a1fc155ccaee17ce6585da
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777007"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="d96e8-102">Método SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="d96e8-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="d96e8-103">Atribui o nome do assembly a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="d96e8-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="d96e8-104">Não para uso na produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="d96e8-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d96e8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d96e8-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d96e8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d96e8-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="d96e8-107">Nome totalmente qualificado do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="d96e8-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="d96e8-108">Ponteiro para interface de [interface IMetaDataEmit](../metadata/imetadataemit-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d96e8-108">Pointer to [IMetaDataEmit Interface](../metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="d96e8-109">Sinalizadores, conforme definido na [Enumeração AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d96e8-109">Flags as defined in [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="d96e8-110">Ponteiro para a ID do assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="d96e8-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d96e8-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d96e8-111">Return Value</span></span>  
 <span data-ttu-id="d96e8-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="d96e8-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d96e8-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d96e8-113">Requirements</span></span>  
 <span data-ttu-id="d96e8-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d96e8-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96e8-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d96e8-115">See also</span></span>

- [<span data-ttu-id="d96e8-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d96e8-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d96e8-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d96e8-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d96e8-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d96e8-118">ALink API</span></span>](index.md)
