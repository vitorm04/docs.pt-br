---
title: Interface ICeeGen
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen
helpviewer_keywords: ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8342c79dd8b7452599af8d9782b0fbec5f83e964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegen-interface"></a><span data-ttu-id="2fb61-102">Interface ICeeGen</span><span class="sxs-lookup"><span data-stu-id="2fb61-102">ICeeGen Interface</span></span>
<span data-ttu-id="2fb61-103">Fornece métodos para compilação de código dinâmico.</span><span class="sxs-lookup"><span data-stu-id="2fb61-103">Provides methods for dynamic code compilation.</span></span>  
  
 <span data-ttu-id="2fb61-104">Esta interface está obsoleta e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-104">This interface is obsolete and should not be used.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2fb61-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="2fb61-105">Methods</span></span>  
  
|<span data-ttu-id="2fb61-106">Método</span><span class="sxs-lookup"><span data-stu-id="2fb61-106">Method</span></span>|<span data-ttu-id="2fb61-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fb61-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2fb61-108">Método AddSectionReloc</span><span class="sxs-lookup"><span data-stu-id="2fb61-108">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|<span data-ttu-id="2fb61-109">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-109">Obsolete.</span></span> <span data-ttu-id="2fb61-110">Adiciona uma instrução de .reloc para a base de código.</span><span class="sxs-lookup"><span data-stu-id="2fb61-110">Adds a .reloc instruction to the code base.</span></span>|  
|[<span data-ttu-id="2fb61-111">Método AllocateMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="2fb61-111">AllocateMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|<span data-ttu-id="2fb61-112">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-112">Obsolete.</span></span> <span data-ttu-id="2fb61-113">Cria um buffer do tamanho especificado para um método e obtém o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="2fb61-113">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>|  
|[<span data-ttu-id="2fb61-114">Método ComputePointer</span><span class="sxs-lookup"><span data-stu-id="2fb61-114">ComputePointer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|<span data-ttu-id="2fb61-115">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-115">Obsolete.</span></span> <span data-ttu-id="2fb61-116">Determina o buffer para a seção de código especificada.</span><span class="sxs-lookup"><span data-stu-id="2fb61-116">Determines the buffer for the specified code section.</span></span>|  
|[<span data-ttu-id="2fb61-117">Método EmitString</span><span class="sxs-lookup"><span data-stu-id="2fb61-117">EmitString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|<span data-ttu-id="2fb61-118">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-118">Obsolete.</span></span> <span data-ttu-id="2fb61-119">Emite a cadeia de caracteres especificada para a base de código.</span><span class="sxs-lookup"><span data-stu-id="2fb61-119">Emits the specified string into the code base.</span></span>|  
|[<span data-ttu-id="2fb61-120">Método GenerateCeeFile</span><span class="sxs-lookup"><span data-stu-id="2fb61-120">GenerateCeeFile Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|<span data-ttu-id="2fb61-121">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-121">Obsolete.</span></span> <span data-ttu-id="2fb61-122">Gera um arquivo de base de código que contém o código base atualmente carregado nisso `ICeeGen`.</span><span class="sxs-lookup"><span data-stu-id="2fb61-122">Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.</span></span>|  
|[<span data-ttu-id="2fb61-123">Método GenerateCeeMemoryImage</span><span class="sxs-lookup"><span data-stu-id="2fb61-123">GenerateCeeMemoryImage Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|<span data-ttu-id="2fb61-124">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-124">Obsolete.</span></span> <span data-ttu-id="2fb61-125">Gera uma imagem na memória para a base de código.</span><span class="sxs-lookup"><span data-stu-id="2fb61-125">Generates an image in memory for the code base.</span></span>|  
|[<span data-ttu-id="2fb61-126">Método GetIlSection</span><span class="sxs-lookup"><span data-stu-id="2fb61-126">GetIlSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|<span data-ttu-id="2fb61-127">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-127">Obsolete.</span></span> <span data-ttu-id="2fb61-128">Obtém a seção do código de idioma intermediário base referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-128">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="2fb61-129">Método GetIMapTokenIface</span><span class="sxs-lookup"><span data-stu-id="2fb61-129">GetIMapTokenIface Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|<span data-ttu-id="2fb61-130">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-130">Obsolete.</span></span> <span data-ttu-id="2fb61-131">Obtém a interface referenciada pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-131">Gets the interface referenced by the specified token.</span></span>|  
|[<span data-ttu-id="2fb61-132">Método GetMethodBuffer</span><span class="sxs-lookup"><span data-stu-id="2fb61-132">GetMethodBuffer Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|<span data-ttu-id="2fb61-133">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-133">Obsolete.</span></span> <span data-ttu-id="2fb61-134">Obtém um buffer de tamanho apropriado para o método no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-134">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="2fb61-135">Método GetSectionBlock</span><span class="sxs-lookup"><span data-stu-id="2fb61-135">GetSectionBlock Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|<span data-ttu-id="2fb61-136">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-136">Obsolete.</span></span> <span data-ttu-id="2fb61-137">Obtém um bloco de seção da base de código.</span><span class="sxs-lookup"><span data-stu-id="2fb61-137">Gets a section block of the code base.</span></span>|  
|[<span data-ttu-id="2fb61-138">Método GetSectionCreate</span><span class="sxs-lookup"><span data-stu-id="2fb61-138">GetSectionCreate Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|<span data-ttu-id="2fb61-139">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-139">Obsolete.</span></span> <span data-ttu-id="2fb61-140">Gera e obtém uma seção de código usando o nome especificado e os valores de sinalizador.</span><span class="sxs-lookup"><span data-stu-id="2fb61-140">Generates and gets a code section using the specified name and flag values.</span></span>|  
|[<span data-ttu-id="2fb61-141">Método GetSectionDataLen</span><span class="sxs-lookup"><span data-stu-id="2fb61-141">GetSectionDataLen Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|<span data-ttu-id="2fb61-142">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-142">Obsolete.</span></span> <span data-ttu-id="2fb61-143">Obtém o comprimento da seção especificada.</span><span class="sxs-lookup"><span data-stu-id="2fb61-143">Gets the length of the specified section.</span></span>|  
|[<span data-ttu-id="2fb61-144">Método GetString</span><span class="sxs-lookup"><span data-stu-id="2fb61-144">GetString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|<span data-ttu-id="2fb61-145">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-145">Obsolete.</span></span> <span data-ttu-id="2fb61-146">Obtém a cadeia de caracteres armazenada no endereço virtual relativo especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-146">Gets the string stored at the specified relative virtual address.</span></span>|  
|[<span data-ttu-id="2fb61-147">Método GetStringSection</span><span class="sxs-lookup"><span data-stu-id="2fb61-147">GetStringSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|<span data-ttu-id="2fb61-148">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-148">Obsolete.</span></span> <span data-ttu-id="2fb61-149">Obtém uma representação de cadeia de caracteres da seção de código referenciada pelo identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-149">Gets a string representation of the code section referenced by the specified handle.</span></span>|  
|[<span data-ttu-id="2fb61-150">Método TruncateSection</span><span class="sxs-lookup"><span data-stu-id="2fb61-150">TruncateSection Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|<span data-ttu-id="2fb61-151">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="2fb61-151">Obsolete.</span></span> <span data-ttu-id="2fb61-152">Trunca a seção de código especificado pelo comprimento especificado.</span><span class="sxs-lookup"><span data-stu-id="2fb61-152">Truncates the specified code section by the specified length.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2fb61-153">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2fb61-153">Requirements</span></span>  
 <span data-ttu-id="2fb61-154">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb61-154">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb61-155">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2fb61-155">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fb61-156">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="2fb61-156">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2fb61-157">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb61-157">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fb61-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2fb61-158">See Also</span></span>  
 [<span data-ttu-id="2fb61-159">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="2fb61-159">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
