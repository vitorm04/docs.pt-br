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
ms.openlocfilehash: 293787d7798768ff2b4e2fb8fec9ed201fdb85ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085409"
---
# <a name="assemblyoptions-enumeration"></a><span data-ttu-id="3df81-102">Enumeração AssemblyOptions</span><span class="sxs-lookup"><span data-stu-id="3df81-102">AssemblyOptions Enumeration</span></span>
<span data-ttu-id="3df81-103">Enumera as opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="3df81-103">Enumerates the assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3df81-104">Syntax</span></span>  
  
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
  
## <a name="fields"></a><span data-ttu-id="3df81-105">Campos</span><span class="sxs-lookup"><span data-stu-id="3df81-105">Fields</span></span>  
  
|<span data-ttu-id="3df81-106">Campo</span><span class="sxs-lookup"><span data-stu-id="3df81-106">Field</span></span>|<span data-ttu-id="3df81-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df81-107">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3df81-108">optAssemTitle</span><span class="sxs-lookup"><span data-stu-id="3df81-108">optAssemTitle</span></span>|<span data-ttu-id="3df81-109">Cadeia de caracteres - representa o título do assembly.</span><span class="sxs-lookup"><span data-stu-id="3df81-109">String - Represents the assembly title.</span></span>|  
|<span data-ttu-id="3df81-110">optAssemDescription</span><span class="sxs-lookup"><span data-stu-id="3df81-110">optAssemDescription</span></span>|<span data-ttu-id="3df81-111">Cadeia de caracteres - contém a descrição do assembly.</span><span class="sxs-lookup"><span data-stu-id="3df81-111">String - Contains the assembly description.</span></span>|  
|<span data-ttu-id="3df81-112">optAssemConfig</span><span class="sxs-lookup"><span data-stu-id="3df81-112">optAssemConfig</span></span>|<span data-ttu-id="3df81-113">Cadeia de caracteres - contém a configuração do assembly.</span><span class="sxs-lookup"><span data-stu-id="3df81-113">String - Contains the assembly configuration.</span></span>|  
|<span data-ttu-id="3df81-114">optAssemOS</span><span class="sxs-lookup"><span data-stu-id="3df81-114">optAssemOS</span></span>|<span data-ttu-id="3df81-115">Cadeia de caracteres, codificada como: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span><span class="sxs-lookup"><span data-stu-id="3df81-115">String - Encoded as: "dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion".</span></span>|  
|<span data-ttu-id="3df81-116">optAssemProcessor</span><span class="sxs-lookup"><span data-stu-id="3df81-116">optAssemProcessor</span></span>|<span data-ttu-id="3df81-117">ULONG</span><span class="sxs-lookup"><span data-stu-id="3df81-117">ULONG</span></span>|  
|<span data-ttu-id="3df81-118">optAssemLocale</span><span class="sxs-lookup"><span data-stu-id="3df81-118">optAssemLocale</span></span>|<span data-ttu-id="3df81-119">Cadeia de caracteres - contém a localidade do assembly.</span><span class="sxs-lookup"><span data-stu-id="3df81-119">String - Contains the assembly locale.</span></span>|  
|<span data-ttu-id="3df81-120">optAssemVersion</span><span class="sxs-lookup"><span data-stu-id="3df81-120">optAssemVersion</span></span>|<span data-ttu-id="3df81-121">Cadeia de caracteres - codificada como: "Major".</span><span class="sxs-lookup"><span data-stu-id="3df81-121">String - Encoded as: "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="3df81-122">optAssemCompany</span><span class="sxs-lookup"><span data-stu-id="3df81-122">optAssemCompany</span></span>|<span data-ttu-id="3df81-123">Cadeia de caracteres - contém a empresa.</span><span class="sxs-lookup"><span data-stu-id="3df81-123">String - Contains the company.</span></span>|  
|<span data-ttu-id="3df81-124">optAssemProduct</span><span class="sxs-lookup"><span data-stu-id="3df81-124">optAssemProduct</span></span>|<span data-ttu-id="3df81-125">Cadeia de caracteres - contém o nome do produto.</span><span class="sxs-lookup"><span data-stu-id="3df81-125">String - Contains the product name.</span></span>|  
|<span data-ttu-id="3df81-126">optAssemProductVersion</span><span class="sxs-lookup"><span data-stu-id="3df81-126">optAssemProductVersion</span></span>|<span data-ttu-id="3df81-127">Cadeia de caracteres (também conhecido como InformationalVersion).</span><span class="sxs-lookup"><span data-stu-id="3df81-127">String (also known as InformationalVersion).</span></span>|  
|<span data-ttu-id="3df81-128">optAssemCopyright</span><span class="sxs-lookup"><span data-stu-id="3df81-128">optAssemCopyright</span></span>|<span data-ttu-id="3df81-129">Cadeia de caracteres - contém as informações de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="3df81-129">String - Contains the copyright information.</span></span>|  
|<span data-ttu-id="3df81-130">optAssemTrademark</span><span class="sxs-lookup"><span data-stu-id="3df81-130">optAssemTrademark</span></span>|<span data-ttu-id="3df81-131">Cadeia de caracteres - contém as informações de marca.</span><span class="sxs-lookup"><span data-stu-id="3df81-131">String - Contains the trademark information.</span></span>|  
|<span data-ttu-id="3df81-132">optAssemKeyFile</span><span class="sxs-lookup"><span data-stu-id="3df81-132">optAssemKeyFile</span></span>|<span data-ttu-id="3df81-133">Cadeia de caracteres (nome de arquivo).</span><span class="sxs-lookup"><span data-stu-id="3df81-133">String (file name).</span></span>|  
|<span data-ttu-id="3df81-134">optAssemKeyName</span><span class="sxs-lookup"><span data-stu-id="3df81-134">optAssemKeyName</span></span>|<span data-ttu-id="3df81-135">Cadeia de caracteres (o nome da chave).</span><span class="sxs-lookup"><span data-stu-id="3df81-135">String (The key name).</span></span>|  
|<span data-ttu-id="3df81-136">optAssemAlgID</span><span class="sxs-lookup"><span data-stu-id="3df81-136">optAssemAlgID</span></span>|<span data-ttu-id="3df81-137">ULONG</span><span class="sxs-lookup"><span data-stu-id="3df81-137">ULONG</span></span>|  
|<span data-ttu-id="3df81-138">optAssemFlags</span><span class="sxs-lookup"><span data-stu-id="3df81-138">optAssemFlags</span></span>|<span data-ttu-id="3df81-139">ULONG</span><span class="sxs-lookup"><span data-stu-id="3df81-139">ULONG</span></span>|  
|<span data-ttu-id="3df81-140">optAssemHalfSign</span><span class="sxs-lookup"><span data-stu-id="3df81-140">optAssemHalfSign</span></span>|<span data-ttu-id="3df81-141">Bool (também conhecido como DelaySign).</span><span class="sxs-lookup"><span data-stu-id="3df81-141">Bool (Also known as DelaySign).</span></span>|  
|<span data-ttu-id="3df81-142">optAssemFileVersion</span><span class="sxs-lookup"><span data-stu-id="3df81-142">optAssemFileVersion</span></span>|<span data-ttu-id="3df81-143">Cadeia de caracteres - codificada como "Major" – mesmo que ProductVersion.</span><span class="sxs-lookup"><span data-stu-id="3df81-143">String - Encoded as "Major.Minor.Build.Revision"--same as ProductVersion.</span></span>|  
|<span data-ttu-id="3df81-144">optAssemSatelliteVer</span><span class="sxs-lookup"><span data-stu-id="3df81-144">optAssemSatelliteVer</span></span>|<span data-ttu-id="3df81-145">Cadeia de caracteres - codificada como "Major".</span><span class="sxs-lookup"><span data-stu-id="3df81-145">String - Encoded as "Major.Minor.Build.Revision".</span></span>|  
|<span data-ttu-id="3df81-146">optLastAssemOption</span><span class="sxs-lookup"><span data-stu-id="3df81-146">optLastAssemOption</span></span>|<span data-ttu-id="3df81-147">Um contador do número de elementos.</span><span class="sxs-lookup"><span data-stu-id="3df81-147">A counter of the number of elements.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3df81-148">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3df81-148">Requirements</span></span>  
 <span data-ttu-id="3df81-149">**Cabeçalho:** alink.h</span><span class="sxs-lookup"><span data-stu-id="3df81-149">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3df81-150">**Biblioteca**: ALink</span><span class="sxs-lookup"><span data-stu-id="3df81-150">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df81-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df81-151">See also</span></span>

- [<span data-ttu-id="3df81-152">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="3df81-152">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
