---
title: Enumeração AssemblyComparisonResult
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178298"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="a10a7-102">Enumeração AssemblyComparisonResult</span><span class="sxs-lookup"><span data-stu-id="a10a7-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="a10a7-103">Indica a equivalência de duas identidades de montagem, conforme determinado pela função [CompareAssemblyIdentity.](compareassemblyidentity-function.md)</span><span class="sxs-lookup"><span data-stu-id="a10a7-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a10a7-104">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="a10a7-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a10a7-105">Members</span></span>  
  
|<span data-ttu-id="a10a7-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="a10a7-106">Member name</span></span>|<span data-ttu-id="a10a7-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a10a7-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="a10a7-108">Indica que todos os campos de montagem na correspondência correspondem.</span><span class="sxs-lookup"><span data-stu-id="a10a7-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="a10a7-109">Indica que os conjuntos são considerados equivalentes com base na unificação da versão de tempo de execução (CLR) com um idioma comum dos números da versão de montagem na versão 2.0 do Framework .NET.</span><span class="sxs-lookup"><span data-stu-id="a10a7-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="a10a7-110">Indica uma correspondência parcial das assembléias com base na unificação clr dos números da versão de montagem no Quadro .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="a10a7-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="a10a7-111">Indica uma combinação parcial das assembléias.</span><span class="sxs-lookup"><span data-stu-id="a10a7-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="a10a7-112">Indica uma correspondência parcial das assembléias baseada na unificação legado dos números das versões.</span><span class="sxs-lookup"><span data-stu-id="a10a7-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="a10a7-113">Indica uma combinação parcial de assembléias simplesmente nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a10a7-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="a10a7-114">Indica que os conjuntos são considerados equivalentes com base na unificação clr de números de versão em versões legadas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a10a7-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="a10a7-115">Indica uma correspondência entre dois conjuntos simplesmente nomeados cujos números de versão foram ignorados.</span><span class="sxs-lookup"><span data-stu-id="a10a7-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="a10a7-116">Indica que não houve correspondência entre as duas assembléias.</span><span class="sxs-lookup"><span data-stu-id="a10a7-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="a10a7-117">Indica que os dois conjuntos correspondem, exceto os números de suas versões, que correspondem apenas parcialmente.</span><span class="sxs-lookup"><span data-stu-id="a10a7-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="a10a7-118">Indica que os dois conjuntos correspondem, exceto os números de suas versões, que não correspondem.</span><span class="sxs-lookup"><span data-stu-id="a10a7-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="a10a7-119">Indica que a razão para a não equivalência não é conhecida.</span><span class="sxs-lookup"><span data-stu-id="a10a7-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a10a7-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a10a7-120">Requirements</span></span>  
 <span data-ttu-id="a10a7-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10a7-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10a7-122">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="a10a7-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a10a7-123">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a10a7-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a10a7-124">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10a7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10a7-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="a10a7-125">See also</span></span>

- [<span data-ttu-id="a10a7-126">Função CompareAssemblyIdentity</span><span class="sxs-lookup"><span data-stu-id="a10a7-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="a10a7-127">Enumerações Fusion</span><span class="sxs-lookup"><span data-stu-id="a10a7-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
