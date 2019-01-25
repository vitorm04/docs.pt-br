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
ms.openlocfilehash: 5fe770ffc5a9c187e9069e8a66553976f9a53b2f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709878"
---
# <a name="setpekind-method"></a><span data-ttu-id="74a81-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="74a81-102">SetPEKind Method</span></span>
<span data-ttu-id="74a81-103">Determina o tipo de executável portátil, específicos do computador ou máquina independente.</span><span class="sxs-lookup"><span data-stu-id="74a81-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="74a81-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="74a81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="74a81-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="74a81-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="74a81-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="74a81-107">Token do arquivo para o qual o tipo de PE deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="74a81-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="74a81-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="74a81-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="74a81-109">O tipo de PE, conforme indicado pelo [enumeração CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="74a81-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="74a81-110">A arquitetura da máquina de destino, conforme indicado no cabeçalho do NT.</span><span class="sxs-lookup"><span data-stu-id="74a81-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74a81-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="74a81-111">Return Value</span></span>  
 <span data-ttu-id="74a81-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="74a81-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a81-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74a81-113">Requirements</span></span>  
 <span data-ttu-id="74a81-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="74a81-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a81-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a81-115">See also</span></span>
- [<span data-ttu-id="74a81-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="74a81-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="74a81-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="74a81-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="74a81-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="74a81-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="74a81-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="74a81-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
