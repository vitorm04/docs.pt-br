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
ms.openlocfilehash: 91dc4cb7d64d49d1e95c0c8eb79a29736559d842
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742089"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="b8712-102">Método EmitManifest</span><span class="sxs-lookup"><span data-stu-id="b8712-102">EmitManifest Method</span></span>
<span data-ttu-id="b8712-103">Emite o manifesto final.</span><span class="sxs-lookup"><span data-stu-id="b8712-103">Emits the final manifest.</span></span> <span data-ttu-id="b8712-104">Chame esse método depois de importar todos os outros arquivos e definir todas as opções.</span><span class="sxs-lookup"><span data-stu-id="b8712-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="b8712-105">Não chame este método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="b8712-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8712-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8712-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8712-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8712-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b8712-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8712-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="b8712-109">Recebe o tamanho para reservar no arquivo de assembly, recuperadas do [função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="b8712-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="b8712-110">Opcionalmente, recebe o token de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8712-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8712-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b8712-111">Return Value</span></span>  
 <span data-ttu-id="b8712-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="b8712-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8712-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8712-113">Requirements</span></span>  
 <span data-ttu-id="b8712-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="b8712-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8712-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8712-115">See also</span></span>

- [<span data-ttu-id="b8712-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="b8712-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b8712-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="b8712-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b8712-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="b8712-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
