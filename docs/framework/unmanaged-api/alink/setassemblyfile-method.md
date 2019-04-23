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
ms.openlocfilehash: a19762cbec91871d7af617957896e4ee34944fba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132698"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="9f45f-102">Método SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="9f45f-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="9f45f-103">Atribui o nome do assembly a ser criado.</span><span class="sxs-lookup"><span data-stu-id="9f45f-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="9f45f-104">Não para uso durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="9f45f-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f45f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f45f-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f45f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f45f-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="9f45f-107">Nome totalmente qualificado do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="9f45f-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="9f45f-108">Ponteiro para [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9f45f-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="9f45f-109">Sinaliza conforme definido em [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9f45f-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="9f45f-110">Ponteiro para a ID do assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="9f45f-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f45f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9f45f-111">Return Value</span></span>  
 <span data-ttu-id="9f45f-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="9f45f-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f45f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f45f-113">Requirements</span></span>  
 <span data-ttu-id="9f45f-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="9f45f-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f45f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f45f-115">See also</span></span>

- [<span data-ttu-id="9f45f-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9f45f-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9f45f-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9f45f-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9f45f-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9f45f-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
