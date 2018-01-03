---
title: "Método ExportType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportType
api_location: alink.dll
api_type: COM
f1_keywords: ExportType
helpviewer_keywords: ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9cc61d0bc32545b486f4472904b17ed0b59526e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exporttype-method"></a><span data-ttu-id="488d2-102">Método ExportType</span><span class="sxs-lookup"><span data-stu-id="488d2-102">ExportType Method</span></span>
<span data-ttu-id="488d2-103">Especifica que um tipo é exportável.</span><span class="sxs-lookup"><span data-stu-id="488d2-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488d2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="488d2-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="488d2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="488d2-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="488d2-106">ID do assembly para exportação.</span><span class="sxs-lookup"><span data-stu-id="488d2-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="488d2-107">Token ou assembly ID de arquivo que define o tipo exportável.</span><span class="sxs-lookup"><span data-stu-id="488d2-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="488d2-108">Token do tipo a ser feita exportável.</span><span class="sxs-lookup"><span data-stu-id="488d2-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="488d2-109">Nome de tipo totalmente qualificado deve ficar exportável.</span><span class="sxs-lookup"><span data-stu-id="488d2-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="488d2-110">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="488d2-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="488d2-111">Esse parâmetro pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="488d2-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="488d2-112">Recebe o token para o tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="488d2-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="488d2-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="488d2-113">Return Value</span></span>  
 <span data-ttu-id="488d2-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="488d2-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488d2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="488d2-115">Requirements</span></span>  
 <span data-ttu-id="488d2-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="488d2-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488d2-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="488d2-117">See Also</span></span>  
 [<span data-ttu-id="488d2-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="488d2-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="488d2-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="488d2-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="488d2-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="488d2-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
