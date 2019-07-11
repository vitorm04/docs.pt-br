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
ms.openlocfilehash: 9876e3ba5ea67442714c2d00b1901c25e54494f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741629"
---
# <a name="importtypes-method"></a><span data-ttu-id="788bb-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="788bb-102">ImportTypes Method</span></span>
<span data-ttu-id="788bb-103">Inicia a importação dos tipos de cada escopo importado por meio [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="788bb-103">Initiates the importing of types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="788bb-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="788bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="788bb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="788bb-106">ID do assembly para importar.</span><span class="sxs-lookup"><span data-stu-id="788bb-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="788bb-107">ID do arquivo de origem.</span><span class="sxs-lookup"><span data-stu-id="788bb-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="788bb-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="788bb-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="788bb-109">Recebe o identificador de enumerador para os tipos neste escopo.</span><span class="sxs-lookup"><span data-stu-id="788bb-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="788bb-110">Opcionalmente, recebe [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="788bb-110">Optionally receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="788bb-111">Opcionalmente, receber a contagem de tipos no escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="788bb-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="788bb-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="788bb-112">Return Value</span></span>  
 <span data-ttu-id="788bb-113">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="788bb-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788bb-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="788bb-114">Requirements</span></span>  
 <span data-ttu-id="788bb-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="788bb-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788bb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="788bb-116">See also</span></span>

- [<span data-ttu-id="788bb-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="788bb-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="788bb-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="788bb-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="788bb-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="788bb-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
