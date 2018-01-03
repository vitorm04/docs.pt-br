---
title: "Método SetAssemblyProps"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyProps
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyProps
helpviewer_keywords: SetAssemblyProps method
ms.assetid: a3d7cf29-1414-49e6-8aae-9b3283c4f5f0
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae13daab0352ad4367c7ad6e06d6c12af23c75bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyprops-method"></a><span data-ttu-id="d7db0-102">Método SetAssemblyProps</span><span class="sxs-lookup"><span data-stu-id="d7db0-102">SetAssemblyProps Method</span></span>
<span data-ttu-id="d7db0-103">Atribui um nível de conjunto de propriedades.</span><span class="sxs-lookup"><span data-stu-id="d7db0-103">Assigns assembly-level properties.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7db0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7db0-104">Syntax</span></span>  
  
```  
HRESULT SetAssemblyProps(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    AssemblyOptions Option,  
    VARIANT         Value  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d7db0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7db0-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d7db0-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d7db0-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d7db0-107">Arquivo que define a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d7db0-107">File that defines the property.</span></span> <span data-ttu-id="d7db0-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="d7db0-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `Option`  
 <span data-ttu-id="d7db0-109">Indica a opção de modificar.</span><span class="sxs-lookup"><span data-stu-id="d7db0-109">Indicates the option to modify.</span></span>  
  
 `Value`  
 <span data-ttu-id="d7db0-110">Novo valor da opção.</span><span class="sxs-lookup"><span data-stu-id="d7db0-110">New value of the option.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7db0-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d7db0-111">Return Value</span></span>  
 <span data-ttu-id="d7db0-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="d7db0-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7db0-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7db0-113">Requirements</span></span>  
 <span data-ttu-id="d7db0-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="d7db0-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7db0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7db0-115">See Also</span></span>  
 [<span data-ttu-id="d7db0-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d7db0-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="d7db0-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d7db0-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="d7db0-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d7db0-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
