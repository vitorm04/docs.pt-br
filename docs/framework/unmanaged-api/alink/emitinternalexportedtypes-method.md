---
title: Método EmitInternalExportedTypes
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55b9d185804f25c7431f2696d67753cc3ba02d1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402035"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="f1200-102">Método EmitInternalExportedTypes</span><span class="sxs-lookup"><span data-stu-id="f1200-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="f1200-103">Emite adicionados ao conjunto de tipos.</span><span class="sxs-lookup"><span data-stu-id="f1200-103">Emits types added to the assembly.</span></span> <span data-ttu-id="f1200-104">Chame este método depois conhecido tipos internos foram adicionados.</span><span class="sxs-lookup"><span data-stu-id="f1200-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1200-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1200-105">Syntax</span></span>  
  
```  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1200-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1200-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f1200-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f1200-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1200-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1200-108">Return Value</span></span>  
 <span data-ttu-id="f1200-109">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f1200-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1200-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1200-110">Requirements</span></span>  
 <span data-ttu-id="f1200-111">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f1200-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1200-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1200-112">See Also</span></span>  
 [<span data-ttu-id="f1200-113">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f1200-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f1200-114">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f1200-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f1200-115">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f1200-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
