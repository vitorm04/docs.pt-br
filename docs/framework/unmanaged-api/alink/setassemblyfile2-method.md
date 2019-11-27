---
title: Método SetAssemblyFile2
ms.date: 03/30/2017
api_name:
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
ms.openlocfilehash: 4f710ef9741869a2b4fd8473ed3ecf379cfcc56d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445588"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="8c7bb-102">Método SetAssemblyFile2</span><span class="sxs-lookup"><span data-stu-id="8c7bb-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="8c7bb-103">Define o nome e as opções para um novo assembly.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="8c7bb-104">Não chame esse método quando você produzir módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c7bb-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8c7bb-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c7bb-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8c7bb-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="8c7bb-107">Nome do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="8c7bb-108">Interface de [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) para este arquivo.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="8c7bb-109">Opções representadas pela [Enumeração AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="8c7bb-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="8c7bb-110">Recebe uma ID exclusiva para o assembly que está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c7bb-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8c7bb-111">Return Value</span></span>  
 <span data-ttu-id="8c7bb-112">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c7bb-113">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8c7bb-113">Requirements</span></span>  
 <span data-ttu-id="8c7bb-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="8c7bb-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c7bb-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8c7bb-115">See also</span></span>

- [<span data-ttu-id="8c7bb-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="8c7bb-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="8c7bb-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="8c7bb-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="8c7bb-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="8c7bb-118">ALink API</span></span>](index.md)
