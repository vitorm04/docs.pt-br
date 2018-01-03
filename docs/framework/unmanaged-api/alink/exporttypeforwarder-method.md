---
title: "Método ExportTypeForwarder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportTypeForwarder
helpviewer_keywords: ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="be51f-102">Método ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="be51f-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="be51f-103">Adiciona um encaminhador de tipo para o tipo de tabela do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="be51f-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be51f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be51f-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be51f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="be51f-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="be51f-106">Referência ao assembly ao qual se refere o encaminhador de tipo.</span><span class="sxs-lookup"><span data-stu-id="be51f-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="be51f-107">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="be51f-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="be51f-108">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="be51f-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="be51f-109">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="be51f-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="be51f-110">Recebe o token do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="be51f-110">Receives the token of the exported type.</span></span> <span data-ttu-id="be51f-111">Isso é necessário apenas para a emissão de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="be51f-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be51f-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="be51f-112">Return Value</span></span>  
 <span data-ttu-id="be51f-113">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="be51f-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be51f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="be51f-114">Requirements</span></span>  
 <span data-ttu-id="be51f-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="be51f-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be51f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be51f-116">See Also</span></span>  
 [<span data-ttu-id="be51f-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="be51f-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="be51f-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="be51f-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="be51f-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="be51f-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
