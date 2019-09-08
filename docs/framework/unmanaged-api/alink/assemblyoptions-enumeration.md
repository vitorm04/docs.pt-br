---
title: Enumeração AssemblyOptions
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 49e7b73559e8def890f8df8f596fbe8ad5bb5d3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777488"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="7ba24-102">Enumeração AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="7ba24-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="7ba24-103">Enumera as opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="7ba24-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ba24-104">Syntax</span></span>  
  
```cpp  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a><span data-ttu-id="7ba24-105">Campos</span><span class="sxs-lookup"><span data-stu-id="7ba24-105">Fields</span></span>  
  
|<span data-ttu-id="7ba24-106">Campo</span><span class="sxs-lookup"><span data-stu-id="7ba24-106">Field</span></span>|<span data-ttu-id="7ba24-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba24-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ba24-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="7ba24-108">optAssemTitle</span></span>|<span data-ttu-id="7ba24-109">String – representa o título do assembly.</span><span class="sxs-lookup"><span data-stu-id="7ba24-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="7ba24-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="7ba24-110">optAssemDescription</span></span>|<span data-ttu-id="7ba24-111">String-contém a descrição do assembly.</span><span class="sxs-lookup"><span data-stu-id="7ba24-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="7ba24-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="7ba24-112">optAssemConfig</span></span>|<span data-ttu-id="7ba24-113">String-contém a configuração do assembly.</span><span class="sxs-lookup"><span data-stu-id="7ba24-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="7ba24-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="7ba24-114">optAssemOS</span></span>|<span data-ttu-id="7ba24-115">Codificada em cadeia de caracteres como: "dwOSPlatformId. dwOSMajorVersion. dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="7ba24-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="7ba24-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="7ba24-116">optAssemProcessor</span></span>|<span data-ttu-id="7ba24-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="7ba24-117">ULONG</span></span>|  
|<span data-ttu-id="7ba24-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="7ba24-118">optAssemLocale</span></span>|<span data-ttu-id="7ba24-119">Cadeia de caracteres – contém a localidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="7ba24-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="7ba24-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="7ba24-120">optAssemVersion</span></span>|<span data-ttu-id="7ba24-121">Codificada em cadeia de caracteres como: "Major. Minor. Build. Revision".</span><span class="sxs-lookup"><span data-stu-id="7ba24-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="7ba24-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="7ba24-122">optAssemCompany</span></span>|<span data-ttu-id="7ba24-123">Cadeia de caracteres – contém a empresa.</span><span class="sxs-lookup"><span data-stu-id="7ba24-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="7ba24-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="7ba24-124">optAssemProduct</span></span>|<span data-ttu-id="7ba24-125">Cadeia de caracteres-contém o nome do produto.</span><span class="sxs-lookup"><span data-stu-id="7ba24-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="7ba24-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="7ba24-126">optAssemProductVersion</span></span>|<span data-ttu-id="7ba24-127">Cadeia de caracteres (também conhecida como InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="7ba24-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="7ba24-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="7ba24-128">optAssemCopyright</span></span>|<span data-ttu-id="7ba24-129">Cadeia de caracteres-contém as informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="7ba24-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="7ba24-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="7ba24-130">optAssemTrademark</span></span>|<span data-ttu-id="7ba24-131">Cadeia de caracteres-contém as informações de marca registrada.</span><span class="sxs-lookup"><span data-stu-id="7ba24-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="7ba24-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="7ba24-132">optAssemKeyFile</span></span>|<span data-ttu-id="7ba24-133">Cadeia de caracteres (nome do arquivo).</span><span class="sxs-lookup"><span data-stu-id="7ba24-133">String (file name).</span></span>|  
|<span data-ttu-id="7ba24-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="7ba24-134">optAssemKeyName</span></span>|<span data-ttu-id="7ba24-135">Cadeia de caracteres (o nome da chave).</span><span class="sxs-lookup"><span data-stu-id="7ba24-135">String (The key name).</span></span>|  
|<span data-ttu-id="7ba24-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="7ba24-136">optAssemAlgID</span></span>|<span data-ttu-id="7ba24-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="7ba24-137">ULONG</span></span>|  
|<span data-ttu-id="7ba24-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="7ba24-138">optAssemFlags</span></span>|<span data-ttu-id="7ba24-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="7ba24-139">ULONG</span></span>|  
|<span data-ttu-id="7ba24-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="7ba24-140">optAssemHalfSign</span></span>|<span data-ttu-id="7ba24-141">Bool (também conhecido como DelaySign).</span><span class="sxs-lookup"><span data-stu-id="7ba24-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="7ba24-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="7ba24-142">optAssemFileVersion</span></span>|<span data-ttu-id="7ba24-143">Cadeia de caracteres codificada como "principal. secundária. Build. Revision" – igual a ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="7ba24-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="7ba24-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="7ba24-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="7ba24-145">Cadeia de caracteres codificada como "principal. secundária. Build. Revision".</span><span class="sxs-lookup"><span data-stu-id="7ba24-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="7ba24-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="7ba24-146">optLastAssemOption</span></span>|<span data-ttu-id="7ba24-147">Um contador do número de elementos.</span><span class="sxs-lookup"><span data-stu-id="7ba24-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ba24-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ba24-148">Requirements</span></span>  
 <span data-ttu-id="7ba24-149">**Cabeçalho:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="7ba24-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="7ba24-150">**Biblioteca**: Alink. dll</span><span class="sxs-lookup"><span data-stu-id="7ba24-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba24-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ba24-151">See also</span></span>

- [<span data-ttu-id="7ba24-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="7ba24-152">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
