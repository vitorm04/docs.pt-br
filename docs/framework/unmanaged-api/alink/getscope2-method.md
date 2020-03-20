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
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179404"
---
# <a name="getscope2-method"></a><span data-ttu-id="ce868-102">Método GetScope2</span><span class="sxs-lookup"><span data-stu-id="ce868-102">GetScope2 Method</span></span>
<span data-ttu-id="ce868-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="ce868-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce868-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce868-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="ce868-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce868-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ce868-106">ID da montagem do alvo.</span><span class="sxs-lookup"><span data-stu-id="ce868-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ce868-107">ID de arquivo a partir do qual importar.</span><span class="sxs-lookup"><span data-stu-id="ce868-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="ce868-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="ce868-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="ce868-109">Recebe ponteiro para interface [IMetaDataImport2](../metadata/imetadataimport2-interface.md) para obter escopo indicado.</span><span class="sxs-lookup"><span data-stu-id="ce868-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce868-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ce868-110">Return Value</span></span>  
 <span data-ttu-id="ce868-111">Retorna S_OK se o método for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="ce868-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce868-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ce868-112">Requirements</span></span>  
 <span data-ttu-id="ce868-113">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="ce868-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce868-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="ce868-114">See also</span></span>

- [<span data-ttu-id="ce868-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="ce868-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="ce868-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="ce868-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="ce868-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="ce868-117">ALink API</span></span>](index.md)
