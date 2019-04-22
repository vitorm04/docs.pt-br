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
ms.openlocfilehash: dec04fa267c61798a3340e9d1e18150b812e9eaf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092650"
---
# <a name="setpekind-method"></a><span data-ttu-id="d88ac-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="d88ac-102">SetPEKind Method</span></span>
<span data-ttu-id="d88ac-103">Determina o tipo de executável portátil, específicos do computador ou máquina independente.</span><span class="sxs-lookup"><span data-stu-id="d88ac-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d88ac-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="d88ac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d88ac-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d88ac-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="d88ac-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="d88ac-107">Token do arquivo para o qual o tipo de PE deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="d88ac-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="d88ac-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="d88ac-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="d88ac-109">O tipo de PE, conforme indicado pelo [enumeração CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="d88ac-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="d88ac-110">A arquitetura da máquina de destino, conforme indicado no cabeçalho do NT.</span><span class="sxs-lookup"><span data-stu-id="d88ac-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d88ac-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d88ac-111">Return Value</span></span>  
 <span data-ttu-id="d88ac-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="d88ac-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d88ac-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d88ac-113">Requirements</span></span>  
 <span data-ttu-id="d88ac-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="d88ac-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88ac-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d88ac-115">See also</span></span>

- [<span data-ttu-id="d88ac-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="d88ac-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="d88ac-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="d88ac-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="d88ac-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="d88ac-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="d88ac-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="d88ac-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
