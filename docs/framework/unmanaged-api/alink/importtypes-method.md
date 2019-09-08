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
ms.openlocfilehash: f19dd114925ed1fd12bcc0056411c3e3d4181215
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777087"
---
# <a name="importtypes-method"></a><span data-ttu-id="00ce8-102">Método ImportTypes</span><span class="sxs-lookup"><span data-stu-id="00ce8-102">ImportTypes Method</span></span>
<span data-ttu-id="00ce8-103">Inicia a importação de tipos de cada escopo importado por meio do [Método ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="00ce8-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ce8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00ce8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="00ce8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="00ce8-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="00ce8-106">ID do assembly para o qual importar.</span><span class="sxs-lookup"><span data-stu-id="00ce8-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="00ce8-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="00ce8-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="00ce8-108">Escopo de base zero para importar.</span><span class="sxs-lookup"><span data-stu-id="00ce8-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="00ce8-109">Recebe o identificador do enumerador para os tipos neste escopo.</span><span class="sxs-lookup"><span data-stu-id="00ce8-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="00ce8-110">Opcionalmente, recebe a interface de [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="00ce8-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="00ce8-111">Opcionalmente, recebe a contagem de tipos no escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="00ce8-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00ce8-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="00ce8-112">Return Value</span></span>  
 <span data-ttu-id="00ce8-113">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="00ce8-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ce8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00ce8-114">Requirements</span></span>  
 <span data-ttu-id="00ce8-115">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="00ce8-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ce8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00ce8-116">See also</span></span>

- [<span data-ttu-id="00ce8-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="00ce8-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="00ce8-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="00ce8-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="00ce8-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="00ce8-119">ALink API</span></span>](index.md)
