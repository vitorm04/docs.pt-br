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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092650"
---
# <a name="setpekind-method"></a><span data-ttu-id="22da4-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="22da4-102">SetPEKind Method</span></span>
<span data-ttu-id="22da4-103">Determina o tipo de executável portátil, específicos do computador ou máquina independente.</span><span class="sxs-lookup"><span data-stu-id="22da4-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22da4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22da4-104">Syntax</span></span>  
  
```  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="22da4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22da4-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="22da4-106">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="22da4-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="22da4-107">Token do arquivo para o qual o tipo de PE deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="22da4-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="22da4-108">Pode ser NULL se `AssemblyID` não indica um netmodule não associado.</span><span class="sxs-lookup"><span data-stu-id="22da4-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="22da4-109">O tipo de PE, conforme indicado pelo [enumeração CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="22da4-109">The type of PE, as indicated by the [CorPEKind Enumeration](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="22da4-110">A arquitetura da máquina de destino, conforme indicado no cabeçalho do NT.</span><span class="sxs-lookup"><span data-stu-id="22da4-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22da4-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="22da4-111">Return Value</span></span>  
 <span data-ttu-id="22da4-112">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="22da4-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22da4-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22da4-113">Requirements</span></span>  
 <span data-ttu-id="22da4-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="22da4-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22da4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22da4-115">See also</span></span>

- [<span data-ttu-id="22da4-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="22da4-116">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="22da4-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="22da4-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="22da4-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="22da4-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="22da4-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="22da4-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
