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
ms.openlocfilehash: a3c6b9e1239dc1baed9428d4fe967eb8274a9304
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789799"
---
# <a name="getscope2-method"></a><span data-ttu-id="1a378-102">Método GetScope2</span><span class="sxs-lookup"><span data-stu-id="1a378-102">GetScope2 Method</span></span>
<span data-ttu-id="1a378-103">Obtém um escopo de importação.</span><span class="sxs-lookup"><span data-stu-id="1a378-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a378-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1a378-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="1a378-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1a378-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1a378-106">ID do assembly de destino.</span><span class="sxs-lookup"><span data-stu-id="1a378-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1a378-107">ID do arquivo do qual importar.</span><span class="sxs-lookup"><span data-stu-id="1a378-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="1a378-108">Escopo baseado em zero para importar.</span><span class="sxs-lookup"><span data-stu-id="1a378-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="1a378-109">Recebe um ponteiro para [Interface IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface para escopo indicada.</span><span class="sxs-lookup"><span data-stu-id="1a378-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a378-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1a378-110">Return Value</span></span>  
 <span data-ttu-id="1a378-111">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="1a378-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a378-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1a378-112">Requirements</span></span>  
 <span data-ttu-id="1a378-113">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="1a378-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a378-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1a378-114">See also</span></span>

- [<span data-ttu-id="1a378-115">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="1a378-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1a378-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="1a378-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1a378-117">API do ALink</span><span class="sxs-lookup"><span data-stu-id="1a378-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
