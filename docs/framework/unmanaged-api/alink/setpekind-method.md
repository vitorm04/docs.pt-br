---
title: Método SetPEKind
ms.date: 03/30/2017
api_name:
- IALink2.SetPEKind
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetPEKind
helpviewer_keywords:
- SetPEKind method
ms.assetid: 050e77ee-3014-45c0-9e29-2ebe29347b0d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fc581904351443f4368a68a653fd39b3548999a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741421"
---
# <a name="setpekind-method"></a><span data-ttu-id="f48c6-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="f48c6-102">SetPEKind Method</span></span>
<span data-ttu-id="f48c6-103">Determina o tipo de executável portátil, específicos do computador ou máquina independente.</span><span class="sxs-lookup"><span data-stu-id="f48c6-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f48c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f48c6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="f48c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f48c6-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f48c6-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f48c6-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f48c6-107">Token do arquivo para o qual o tipo de PE deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="f48c6-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="f48c6-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="f48c6-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="f48c6-109">O tipo de PE, conforme indicado pelo [enumeração CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f48c6-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="f48c6-110">A arquitetura da máquina de destino, conforme indicado no cabeçalho do NT.</span><span class="sxs-lookup"><span data-stu-id="f48c6-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f48c6-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f48c6-111">Return Value</span></span>  
 <span data-ttu-id="f48c6-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="f48c6-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f48c6-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f48c6-113">Requirements</span></span>  
 <span data-ttu-id="f48c6-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="f48c6-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48c6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f48c6-115">See also</span></span>

- [<span data-ttu-id="f48c6-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="f48c6-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="f48c6-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f48c6-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="f48c6-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f48c6-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="f48c6-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f48c6-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
