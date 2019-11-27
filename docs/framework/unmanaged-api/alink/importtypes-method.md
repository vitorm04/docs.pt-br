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
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445684"
---
# <a name="importtypes-method"></a><span data-ttu-id="6e409-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="6e409-102">ImportTypes Method</span></span>
<span data-ttu-id="6e409-103">Inicia a importação de tipos de cada escopo importado por meio do [Método ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="6e409-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e409-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6e409-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="6e409-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6e409-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6e409-106">ID do assembly para o qual importar.</span><span class="sxs-lookup"><span data-stu-id="6e409-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6e409-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="6e409-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="6e409-108">Escopo de base zero para importar.</span><span class="sxs-lookup"><span data-stu-id="6e409-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="6e409-109">Recebe o identificador do enumerador para os tipos neste escopo.</span><span class="sxs-lookup"><span data-stu-id="6e409-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="6e409-110">Opcionalmente, recebe a interface de [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6e409-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="6e409-111">Opcionalmente, recebe a contagem de tipos no escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="6e409-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e409-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6e409-112">Return Value</span></span>  
 <span data-ttu-id="6e409-113">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="6e409-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e409-114">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="6e409-114">Requirements</span></span>  
 <span data-ttu-id="6e409-115">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="6e409-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e409-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e409-116">See also</span></span>

- [<span data-ttu-id="6e409-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="6e409-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="6e409-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="6e409-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="6e409-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="6e409-119">ALink API</span></span>](index.md)
