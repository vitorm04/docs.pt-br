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
ms.openlocfilehash: 59bfc6785d3ad195e219afc323b7fdb513d8fefc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949052"
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="a896f-102">Método SetAssemblyFile2</span><span class="sxs-lookup"><span data-stu-id="a896f-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="a896f-103">Define o nome e as opções para um novo assembly.</span><span class="sxs-lookup"><span data-stu-id="a896f-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="a896f-104">Não chame este método quando você produzir módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="a896f-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a896f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a896f-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a896f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a896f-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="a896f-107">Nome do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="a896f-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="a896f-108">[Interface IMetaDataEmit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface para esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="a896f-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="a896f-109">Opções de representado por [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a896f-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="a896f-110">Recebe a ID exclusiva para o assembly que está sendo construído.</span><span class="sxs-lookup"><span data-stu-id="a896f-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a896f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a896f-111">Return Value</span></span>  
 <span data-ttu-id="a896f-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="a896f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a896f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a896f-113">Requirements</span></span>  
 <span data-ttu-id="a896f-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="a896f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a896f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a896f-115">See also</span></span>

- [<span data-ttu-id="a896f-116">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="a896f-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a896f-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="a896f-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a896f-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="a896f-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
