---
title: "Método EmbedResource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 98dbd32452184bf4f832bd66ffebb0fcf3d5bb0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="71fcd-102">Método EmbedResource</span><span class="sxs-lookup"><span data-stu-id="71fcd-102">EmbedResource Method</span></span>
<span data-ttu-id="71fcd-103">Declara um recurso inserido.</span><span class="sxs-lookup"><span data-stu-id="71fcd-103">Declares an embedded resource.</span></span> <span data-ttu-id="71fcd-104">Esse método não insere, na verdade, o recurso.</span><span class="sxs-lookup"><span data-stu-id="71fcd-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71fcd-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="71fcd-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71fcd-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="71fcd-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="71fcd-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="71fcd-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="71fcd-108">ID de token ou assembly de arquivo que contém o recurso do arquivo.</span><span class="sxs-lookup"><span data-stu-id="71fcd-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="71fcd-109">Nome do recurso.</span><span class="sxs-lookup"><span data-stu-id="71fcd-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="71fcd-110">Deslocamento do recurso do RVA.</span><span class="sxs-lookup"><span data-stu-id="71fcd-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="71fcd-111">Acessibilidade como sinalizadores `mrPublic` e `mrPrivate`.</span><span class="sxs-lookup"><span data-stu-id="71fcd-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="71fcd-112">Esses sinalizadores podem ser passados para [método DefineExportedType](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="71fcd-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71fcd-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="71fcd-113">Return Value</span></span>  
 <span data-ttu-id="71fcd-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="71fcd-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71fcd-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="71fcd-115">Requirements</span></span>  
 <span data-ttu-id="71fcd-116">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="71fcd-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71fcd-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71fcd-117">See Also</span></span>  
 [<span data-ttu-id="71fcd-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="71fcd-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="71fcd-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="71fcd-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="71fcd-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="71fcd-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
