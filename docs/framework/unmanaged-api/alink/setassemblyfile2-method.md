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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aba11ccd61b65d2a779b39db8e0e082cf4d4015b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787221"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="3d9c3-102">Método SetAssemblyFile2</span><span class="sxs-lookup"><span data-stu-id="3d9c3-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="3d9c3-103">Define o nome e as opções para um novo assembly.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="3d9c3-104">Não chame esse método quando você produzir módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9c3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3d9c3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d9c3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3d9c3-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="3d9c3-107">Nome do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="3d9c3-108">Interface de [interface IMetaDataEmit2](../metadata/imetadataemit2-interface.md) para este arquivo.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-108">[IMetaDataEmit2 Interface](../metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="3d9c3-109">Opções representadas pela [Enumeração AssemblyFlags](../metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="3d9c3-109">Options represented by [AssemblyFlags Enumeration](../metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="3d9c3-110">Recebe uma ID exclusiva para o assembly que está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d9c3-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3d9c3-111">Return Value</span></span>  
 <span data-ttu-id="3d9c3-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d9c3-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3d9c3-113">Requirements</span></span>  
 <span data-ttu-id="3d9c3-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="3d9c3-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d9c3-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3d9c3-115">See also</span></span>

- [<span data-ttu-id="3d9c3-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="3d9c3-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="3d9c3-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3d9c3-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="3d9c3-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="3d9c3-118">ALink API</span></span>](index.md)
