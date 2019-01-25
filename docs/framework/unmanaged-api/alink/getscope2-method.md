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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cc986dc27deb08f779a9654324e6832d8420554a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587122"
---
# <a name="getscope2-method"></a><span data-ttu-id="147a1-102">Método GetScope2</span><span class="sxs-lookup"><span data-stu-id="147a1-102">GetScope2 Method</span></span>
<span data-ttu-id="147a1-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="147a1-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="147a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="147a1-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="147a1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="147a1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="147a1-106">ID do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="147a1-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="147a1-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="147a1-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="147a1-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="147a1-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="147a1-109">Recebe um ponteiro para [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface para escopo indicada.</span><span class="sxs-lookup"><span data-stu-id="147a1-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="147a1-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="147a1-110">Return Value</span></span>  
 <span data-ttu-id="147a1-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="147a1-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="147a1-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="147a1-112">Requirements</span></span>  
 <span data-ttu-id="147a1-113">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="147a1-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147a1-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="147a1-114">See also</span></span>
- [<span data-ttu-id="147a1-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="147a1-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="147a1-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="147a1-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="147a1-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="147a1-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
