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
ms.openlocfilehash: bdab1fd10be8fd245f4348798232964721b4487a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777345"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="d4d04-102">Método EmitManifest</span><span class="sxs-lookup"><span data-stu-id="d4d04-102">EmitManifest Method</span></span>
<span data-ttu-id="d4d04-103">Emite o manifesto final.</span><span class="sxs-lookup"><span data-stu-id="d4d04-103">Emits the final manifest.</span></span> <span data-ttu-id="d4d04-104">Chame esse método depois de importar todos os outros arquivos e definir todas as opções.</span><span class="sxs-lookup"><span data-stu-id="d4d04-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="d4d04-105">Não chame esse método para módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="d4d04-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d04-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4d04-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4d04-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4d04-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d4d04-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d4d04-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="d4d04-109">Recebe o tamanho a ser reservado no arquivo de assembly, recuperado da [função StrongNameSignatureSize](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="d4d04-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="d4d04-110">Opcionalmente, recebe o token do manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d4d04-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4d04-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d4d04-111">Return Value</span></span>  
 <span data-ttu-id="d4d04-112">Retornará S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="d4d04-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4d04-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4d04-113">Requirements</span></span>  
 <span data-ttu-id="d4d04-114">Requer ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d4d04-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d04-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4d04-115">See also</span></span>

- [<span data-ttu-id="d4d04-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d4d04-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d4d04-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d4d04-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d4d04-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d4d04-118">ALink API</span></span>](index.md)
