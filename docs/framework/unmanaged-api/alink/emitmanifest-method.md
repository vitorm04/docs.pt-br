---
title: Método EmitManifest
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 051b5f47db05301f3a3326a2cc4cc5cf5c8b1ec2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137820"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="2a3bc-102">Método EmitManifest</span><span class="sxs-lookup"><span data-stu-id="2a3bc-102">EmitManifest Method</span></span>
<span data-ttu-id="2a3bc-103">Emite o manifesto final.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-103">Emits the final manifest.</span></span> <span data-ttu-id="2a3bc-104">Chame esse método depois de importar todos os outros arquivos e definir todas as opções.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="2a3bc-105">Não chame este método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a3bc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a3bc-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a3bc-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a3bc-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2a3bc-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="2a3bc-109">Recebe o tamanho para reservar no arquivo de assembly, recuperadas do [função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="2a3bc-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="2a3bc-110">Opcionalmente, recebe o token de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a3bc-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2a3bc-111">Return Value</span></span>  
 <span data-ttu-id="2a3bc-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a3bc-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a3bc-113">Requirements</span></span>  
 <span data-ttu-id="2a3bc-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="2a3bc-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3bc-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a3bc-115">See also</span></span>

- [<span data-ttu-id="2a3bc-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="2a3bc-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="2a3bc-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="2a3bc-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="2a3bc-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="2a3bc-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
