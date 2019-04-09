---
title: Método ImportTypes2
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f14822a58f3982d6f9fee1328c10b960657c056f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098462"
---
# <a name="importtypes2-method"></a><span data-ttu-id="136f9-102">Método ImportTypes2</span><span class="sxs-lookup"><span data-stu-id="136f9-102">ImportTypes2 Method</span></span>
<span data-ttu-id="136f9-103">Inicia a importação de tipos.</span><span class="sxs-lookup"><span data-stu-id="136f9-103">Initiates the import of types.</span></span> <span data-ttu-id="136f9-104">Chame esse método para começar a importar tipos de cada escopo importado por meio [método ImportFile](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="136f9-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136f9-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="136f9-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="136f9-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="136f9-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="136f9-107">ID do assembly no qual importar.</span><span class="sxs-lookup"><span data-stu-id="136f9-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="136f9-108">ID do arquivo a partir do qual importar.</span><span class="sxs-lookup"><span data-stu-id="136f9-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="136f9-109">Escopo baseado em zero do qual importar.</span><span class="sxs-lookup"><span data-stu-id="136f9-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="136f9-110">Recebe o identificador de enumerador para os tipos no escopo fornecido.</span><span class="sxs-lookup"><span data-stu-id="136f9-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="136f9-111">Opcionalmente, recebe [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="136f9-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="136f9-112">Opcionalmente, recebe a contagem de tipos no escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="136f9-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="136f9-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="136f9-113">Return Value</span></span>  
 <span data-ttu-id="136f9-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="136f9-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136f9-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="136f9-115">Requirements</span></span>  
 <span data-ttu-id="136f9-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="136f9-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136f9-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="136f9-117">See also</span></span>

- [<span data-ttu-id="136f9-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="136f9-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="136f9-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="136f9-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="136f9-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="136f9-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
