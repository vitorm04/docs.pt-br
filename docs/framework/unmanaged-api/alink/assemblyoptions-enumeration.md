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
ms.openlocfilehash: 939e815f4d3adc5f6e1c8b8fc85c9f4b89372501
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571477"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="b8112-102">Enumeração AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="b8112-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="b8112-103">Enumera as opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="b8112-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8112-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8112-104">Syntax</span></span>  
  
```  
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
  
## <a name="fields"></a><span data-ttu-id="b8112-105">Campos</span><span class="sxs-lookup"><span data-stu-id="b8112-105">Fields</span></span>  
  
|<span data-ttu-id="b8112-106">Campo</span><span class="sxs-lookup"><span data-stu-id="b8112-106">Field</span></span>|<span data-ttu-id="b8112-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8112-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8112-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="b8112-108">optAssemTitle</span></span>|<span data-ttu-id="b8112-109">Cadeia de caracteres - representa o título do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8112-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="b8112-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="b8112-110">optAssemDescription</span></span>|<span data-ttu-id="b8112-111">Cadeia de caracteres - contém a descrição do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8112-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="b8112-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="b8112-112">optAssemConfig</span></span>|<span data-ttu-id="b8112-113">Cadeia de caracteres - contém a configuração do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8112-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="b8112-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="b8112-114">optAssemOS</span></span>|<span data-ttu-id="b8112-115">Cadeia de caracteres, codificada como: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="b8112-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="b8112-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="b8112-116">optAssemProcessor</span></span>|<span data-ttu-id="b8112-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="b8112-117">ULONG</span></span>|  
|<span data-ttu-id="b8112-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="b8112-118">optAssemLocale</span></span>|<span data-ttu-id="b8112-119">Cadeia de caracteres - contém a localidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="b8112-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="b8112-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="b8112-120">optAssemVersion</span></span>|<span data-ttu-id="b8112-121">Cadeia de caracteres - codificada como: "Major".</span><span class="sxs-lookup"><span data-stu-id="b8112-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="b8112-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="b8112-122">optAssemCompany</span></span>|<span data-ttu-id="b8112-123">Cadeia de caracteres - contém a empresa.</span><span class="sxs-lookup"><span data-stu-id="b8112-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="b8112-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="b8112-124">optAssemProduct</span></span>|<span data-ttu-id="b8112-125">Cadeia de caracteres - contém o nome do produto.</span><span class="sxs-lookup"><span data-stu-id="b8112-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="b8112-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="b8112-126">optAssemProductVersion</span></span>|<span data-ttu-id="b8112-127">Cadeia de caracteres (também conhecido como InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="b8112-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="b8112-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="b8112-128">optAssemCopyright</span></span>|<span data-ttu-id="b8112-129">Cadeia de caracteres - contém as informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="b8112-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="b8112-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="b8112-130">optAssemTrademark</span></span>|<span data-ttu-id="b8112-131">Cadeia de caracteres - contém as informações de marca.</span><span class="sxs-lookup"><span data-stu-id="b8112-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="b8112-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="b8112-132">optAssemKeyFile</span></span>|<span data-ttu-id="b8112-133">Cadeia de caracteres (nome de arquivo).</span><span class="sxs-lookup"><span data-stu-id="b8112-133">String (file name).</span></span>|  
|<span data-ttu-id="b8112-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="b8112-134">optAssemKeyName</span></span>|<span data-ttu-id="b8112-135">Cadeia de caracteres (o nome da chave).</span><span class="sxs-lookup"><span data-stu-id="b8112-135">String (The key name).</span></span>|  
|<span data-ttu-id="b8112-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="b8112-136">optAssemAlgID</span></span>|<span data-ttu-id="b8112-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="b8112-137">ULONG</span></span>|  
|<span data-ttu-id="b8112-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="b8112-138">optAssemFlags</span></span>|<span data-ttu-id="b8112-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="b8112-139">ULONG</span></span>|  
|<span data-ttu-id="b8112-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="b8112-140">optAssemHalfSign</span></span>|<span data-ttu-id="b8112-141">Bool (também conhecido como DelaySign).</span><span class="sxs-lookup"><span data-stu-id="b8112-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="b8112-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="b8112-142">optAssemFileVersion</span></span>|<span data-ttu-id="b8112-143">Cadeia de caracteres - codificada como "Major" – mesmo que ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="b8112-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="b8112-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="b8112-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="b8112-145">Cadeia de caracteres - codificada como "Major".</span><span class="sxs-lookup"><span data-stu-id="b8112-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="b8112-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="b8112-146">optLastAssemOption</span></span>|<span data-ttu-id="b8112-147">Um contador do número de elementos.</span><span class="sxs-lookup"><span data-stu-id="b8112-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b8112-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8112-148">Requirements</span></span>  
 <span data-ttu-id="b8112-149">**Cabeçalho:** alink.h</span><span class="sxs-lookup"><span data-stu-id="b8112-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="b8112-150">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="b8112-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8112-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8112-151">See also</span></span>
- [<span data-ttu-id="b8112-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="b8112-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
