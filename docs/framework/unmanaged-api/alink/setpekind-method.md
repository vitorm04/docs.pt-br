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
ms.openlocfilehash: 5a8442b1f0869e1592a05dfeeb0f5e6d583f3ea8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179383"
---
# <a name="setpekind-method"></a><span data-ttu-id="56a76-102">Método SetPEKind</span><span class="sxs-lookup"><span data-stu-id="56a76-102">SetPEKind Method</span></span>
<span data-ttu-id="56a76-103">Determina o tipo executável portátil, específico da máquina ou agnóstico da máquina.</span><span class="sxs-lookup"><span data-stu-id="56a76-103">Determines the portable executable type, either machine-specific or machine-agnostic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a76-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56a76-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPEKind(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwPEKind,  
    DWORD dwMachine  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="56a76-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="56a76-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="56a76-106">ID da assembléia.</span><span class="sxs-lookup"><span data-stu-id="56a76-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="56a76-107">Token de arquivo para o qual o tipo PE deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="56a76-107">Token of file for which the PE type is to be set.</span></span> <span data-ttu-id="56a76-108">Pode ser `AssemblyID` NULO se não indicar um módulo de rede não vinculado.</span><span class="sxs-lookup"><span data-stu-id="56a76-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `dwPEKind`  
 <span data-ttu-id="56a76-109">O tipo de PE, conforme indicado pela [Enumeração CorPEKind](../metadata/corpekind-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="56a76-109">The type of PE, as indicated by the [CorPEKind Enumeration](../metadata/corpekind-enumeration.md).</span></span>  
  
 `dwMachine`  
 <span data-ttu-id="56a76-110">A arquitetura da máquina de destino, conforme indicado no cabeçalho NT.</span><span class="sxs-lookup"><span data-stu-id="56a76-110">The target machine architecture, as indicated in the NT header.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56a76-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="56a76-111">Return Value</span></span>  
 <span data-ttu-id="56a76-112">Retorna S_OK se o método for bem sucedido.</span><span class="sxs-lookup"><span data-stu-id="56a76-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56a76-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="56a76-113">Requirements</span></span>  
 <span data-ttu-id="56a76-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="56a76-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a76-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="56a76-115">See also</span></span>

- [<span data-ttu-id="56a76-116">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="56a76-116">GetPEKind Method</span></span>](../metadata/imetadataimport2-getpekind-method.md)
- [<span data-ttu-id="56a76-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="56a76-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="56a76-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="56a76-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="56a76-119">API do ALink</span><span class="sxs-lookup"><span data-stu-id="56a76-119">ALink API</span></span>](index.md)
