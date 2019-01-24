---
title: Método ImportTypes
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6591fb4a2b4944dc0d02f70f0f90ffd87e071c47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734994"
---
# <a name="importtypes-method"></a><span data-ttu-id="5d742-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="5d742-102">ImportTypes Method</span></span>
<span data-ttu-id="5d742-103">Inicia a importação dos tipos de cada escopo importado por meio [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="5d742-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d742-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d742-104">Syntax</span></span>  
  
```  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d742-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5d742-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5d742-106">ID do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="5d742-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5d742-107">ID do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="5d742-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="5d742-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="5d742-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="5d742-109">Recebe o identificador de enumerador para os tipos neste escopo.</span><span class="sxs-lookup"><span data-stu-id="5d742-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="5d742-110">Opcionalmente, recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="5d742-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="5d742-111">Opcionalmente, receber a contagem de tipos no escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="5d742-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d742-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5d742-112">Return Value</span></span>  
 <span data-ttu-id="5d742-113">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="5d742-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d742-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5d742-114">Requirements</span></span>  
 <span data-ttu-id="5d742-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="5d742-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d742-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d742-116">See also</span></span>
- [<span data-ttu-id="5d742-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="5d742-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="5d742-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="5d742-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="5d742-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="5d742-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
