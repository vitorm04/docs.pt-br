---
title: Método GetScope2
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
ms.openlocfilehash: a5b080443be94d5a298cc67591914d87470e6f48
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447192"
---
# <a name="getscope2-method"></a><span data-ttu-id="b0cbb-102">Método GetScope2</span><span class="sxs-lookup"><span data-stu-id="b0cbb-102">GetScope2 Method</span></span>
<span data-ttu-id="b0cbb-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0cbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b0cbb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="b0cbb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b0cbb-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b0cbb-106">ID do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b0cbb-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="b0cbb-108">Escopo de base zero para importar.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="b0cbb-109">Recebe o ponteiro para a interface de [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) para o escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b0cbb-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b0cbb-110">Return Value</span></span>  
 <span data-ttu-id="b0cbb-111">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0cbb-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="b0cbb-112">Requirements</span></span>  
 <span data-ttu-id="b0cbb-113">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="b0cbb-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0cbb-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0cbb-114">See also</span></span>

- [<span data-ttu-id="b0cbb-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="b0cbb-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b0cbb-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="b0cbb-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b0cbb-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="b0cbb-117">ALink API</span></span>](index.md)
