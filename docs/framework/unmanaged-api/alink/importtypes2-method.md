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
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787262"
---
# <a name="importtypes2-method"></a><span data-ttu-id="f30c5-102">Método ImportTypes2</span><span class="sxs-lookup"><span data-stu-id="f30c5-102">ImportTypes2 Method</span></span>
<span data-ttu-id="f30c5-103">Inicia a importação de tipos.</span><span class="sxs-lookup"><span data-stu-id="f30c5-103">Initiates the import of types.</span></span> <span data-ttu-id="f30c5-104">Chame esse método para começar a importar tipos de cada escopo importado por meio do [Método ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="f30c5-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f30c5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f30c5-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="f30c5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f30c5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f30c5-107">ID do assembly no qual importar.</span><span class="sxs-lookup"><span data-stu-id="f30c5-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f30c5-108">ID do arquivo a partir do qual importar.</span><span class="sxs-lookup"><span data-stu-id="f30c5-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="f30c5-109">Escopo de base zero do qual importar.</span><span class="sxs-lookup"><span data-stu-id="f30c5-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="f30c5-110">Recebe o identificador do enumerador para os tipos no escopo fornecido.</span><span class="sxs-lookup"><span data-stu-id="f30c5-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="f30c5-111">Opcionalmente, recebe a interface de [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="f30c5-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="f30c5-112">Opcionalmente, recebe a contagem de tipos no escopo especificado.</span><span class="sxs-lookup"><span data-stu-id="f30c5-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f30c5-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f30c5-113">Return Value</span></span>  
 <span data-ttu-id="f30c5-114">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="f30c5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f30c5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f30c5-115">Requirements</span></span>  
 <span data-ttu-id="f30c5-116">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="f30c5-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f30c5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f30c5-117">See also</span></span>

- [<span data-ttu-id="f30c5-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f30c5-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="f30c5-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f30c5-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="f30c5-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f30c5-120">ALink API</span></span>](index.md)
