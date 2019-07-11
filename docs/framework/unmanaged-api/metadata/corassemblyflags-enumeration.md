---
title: Enumeração CorAssemblyFlags
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3532ca0a30d83aa8f61bc4397090f3d589b73257
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780927"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="4acc3-102">Enumeração CorAssemblyFlags</span><span class="sxs-lookup"><span data-stu-id="4acc3-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="4acc3-103">Contém valores que descrevem os metadados aplicados a uma compilação do assembly.</span><span class="sxs-lookup"><span data-stu-id="4acc3-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4acc3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4acc3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="4acc3-105">Membros</span><span class="sxs-lookup"><span data-stu-id="4acc3-105">Members</span></span>  
  
|<span data-ttu-id="4acc3-106">Membro</span><span class="sxs-lookup"><span data-stu-id="4acc3-106">Member</span></span>|<span data-ttu-id="4acc3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4acc3-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="4acc3-108">Indica que a referência de assembly retém a chave pública completa, sem hash.</span><span class="sxs-lookup"><span data-stu-id="4acc3-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="4acc3-109">Indica que a arquitetura do processador é especificada.</span><span class="sxs-lookup"><span data-stu-id="4acc3-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="4acc3-110">Indica que a arquitetura do processador é neutra (PE32).</span><span class="sxs-lookup"><span data-stu-id="4acc3-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="4acc3-111">Indica que a arquitetura de processador x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="4acc3-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="4acc3-112">Indica que a arquitetura do processador Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="4acc3-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="4acc3-113">Indica que a arquitetura do processador AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="4acc3-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="4acc3-114">Indica que a arquitetura do processador ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="4acc3-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="4acc3-115">Indica que o assembly é um assembly de referência; ou seja, ele se aplica a qualquer arquitetura, mas não pode ser executado em qualquer arquitetura.</span><span class="sxs-lookup"><span data-stu-id="4acc3-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="4acc3-116">Portanto, o sinalizador é o mesmo que `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="4acc3-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="4acc3-117">Indica que os sinalizadores de arquitetura de processador devem ser propagados para o `AssemblyRef` registro.</span><span class="sxs-lookup"><span data-stu-id="4acc3-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="4acc3-118">Uma máscara que descreve a arquitetura do processador.</span><span class="sxs-lookup"><span data-stu-id="4acc3-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="4acc3-119">Especifica que a descrição da arquitetura de processador está incluída.</span><span class="sxs-lookup"><span data-stu-id="4acc3-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="4acc3-120">Indica uma contagem de shift os sinalizadores de arquitetura do processador de e para o índice.</span><span class="sxs-lookup"><span data-stu-id="4acc3-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="4acc3-121">Indica o valor correspondente do <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> do <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4acc3-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="4acc3-122">Indica o valor correspondente do <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> do <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4acc3-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="4acc3-123">Indica que o assembly pode ser redirecionado em tempo de execução a um assembly de um outro editor.</span><span class="sxs-lookup"><span data-stu-id="4acc3-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="4acc3-124">Uma máscara que descreve o tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="4acc3-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="4acc3-125">Indica o tipo de conteúdo padrão.</span><span class="sxs-lookup"><span data-stu-id="4acc3-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="4acc3-126">Indica o tipo de conteúdo de tempo de execução do Windows.</span><span class="sxs-lookup"><span data-stu-id="4acc3-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4acc3-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4acc3-127">Requirements</span></span>  
 <span data-ttu-id="4acc3-128">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4acc3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4acc3-129">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4acc3-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4acc3-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4acc3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4acc3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4acc3-131">See also</span></span>

- [<span data-ttu-id="4acc3-132">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="4acc3-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
