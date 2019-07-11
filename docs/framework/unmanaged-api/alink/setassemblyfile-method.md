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
ms.openlocfilehash: b7be346f1c92c877932957787b0747515c144752
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741539"
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="9039e-102">Método SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="9039e-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="9039e-103">Atribui o nome do assembly a ser criado.</span><span class="sxs-lookup"><span data-stu-id="9039e-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="9039e-104">Não para uso durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="9039e-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9039e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9039e-105">Syntax</span></span>  
  
```cpp  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9039e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9039e-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="9039e-107">Nome totalmente qualificado do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="9039e-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="9039e-108">Ponteiro para [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9039e-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="9039e-109">Sinaliza conforme definido em [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="9039e-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="9039e-110">Ponteiro para a ID do assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="9039e-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9039e-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9039e-111">Return Value</span></span>  
 <span data-ttu-id="9039e-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="9039e-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9039e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9039e-113">Requirements</span></span>  
 <span data-ttu-id="9039e-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="9039e-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9039e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9039e-115">See also</span></span>

- [<span data-ttu-id="9039e-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="9039e-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9039e-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="9039e-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9039e-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="9039e-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
