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
ms.openlocfilehash: 1e557cc0da7bc684843ae3969242ffb84d811c44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405340"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="e0656-102">Método SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="e0656-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="e0656-103">Atribui o nome do assembly a ser criado.</span><span class="sxs-lookup"><span data-stu-id="e0656-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="e0656-104">Não para uso durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="e0656-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0656-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0656-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0656-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0656-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="e0656-107">Nome totalmente qualificado do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="e0656-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="e0656-108">Ponteiro para [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e0656-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="e0656-109">Sinalizadores conforme definido em [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e0656-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="e0656-110">Ponteiro para a ID do assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="e0656-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0656-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e0656-111">Return Value</span></span>  
 <span data-ttu-id="e0656-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="e0656-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0656-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0656-113">Requirements</span></span>  
 <span data-ttu-id="e0656-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="e0656-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0656-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0656-115">See Also</span></span>  
 [<span data-ttu-id="e0656-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="e0656-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e0656-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="e0656-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e0656-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="e0656-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
