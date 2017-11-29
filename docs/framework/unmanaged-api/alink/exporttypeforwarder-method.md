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
ms.openlocfilehash: 0f117d64673729113d917d700e3a26f9723b5a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="83c49-102">Método ExportTypeForwarder</span><span class="sxs-lookup"><span data-stu-id="83c49-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="83c49-103">Adiciona um encaminhador de tipo para o tipo de tabela do assembly fornecido.</span><span class="sxs-lookup"><span data-stu-id="83c49-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c49-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="83c49-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83c49-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="83c49-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="83c49-106">Referência ao assembly ao qual se refere o encaminhador de tipo.</span><span class="sxs-lookup"><span data-stu-id="83c49-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="83c49-107">Nome de tipo totalmente qualificado para exportar.</span><span class="sxs-lookup"><span data-stu-id="83c49-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="83c49-108">`ComType`sinalizadores como `tdPublic` ou `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="83c49-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="83c49-109">Esse valor pode ser passado para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="83c49-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="83c49-110">Recebe o token do tipo exportado.</span><span class="sxs-lookup"><span data-stu-id="83c49-110">Receives the token of the exported type.</span></span> <span data-ttu-id="83c49-111">Isso é necessário apenas para a emissão de tipos aninhados.</span><span class="sxs-lookup"><span data-stu-id="83c49-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83c49-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="83c49-112">Return Value</span></span>  
 <span data-ttu-id="83c49-113">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="83c49-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83c49-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="83c49-114">Requirements</span></span>  
 <span data-ttu-id="83c49-115">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="83c49-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c49-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83c49-116">See Also</span></span>  
 [<span data-ttu-id="83c49-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="83c49-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="83c49-118">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="83c49-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="83c49-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="83c49-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
