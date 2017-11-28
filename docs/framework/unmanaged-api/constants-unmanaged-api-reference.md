---
title: "Constantes (referência de API não gerenciada)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45e4d41c16695010dc452d2f22850d43f885974a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="48c05-102">Constantes (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="48c05-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="48c05-103">Este tópico descreve o tipo de idioma, fornecedor de linguagem e constantes de tipo de documento que são definidos em CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="48c05-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="48c05-104">Constantes de tipo de linguagem</span><span class="sxs-lookup"><span data-stu-id="48c05-104">Language Type Constants</span></span>  
 <span data-ttu-id="48c05-105">A tabela a seguir mostra a linguagem de constantes de tipo, que representam os GUIDs que identificam as linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="48c05-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="48c05-106">Símbolo</span><span class="sxs-lookup"><span data-stu-id="48c05-106">Symbol</span></span>|<span data-ttu-id="48c05-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48c05-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="48c05-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="48c05-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="48c05-109">Indica a linguagem C.</span><span class="sxs-lookup"><span data-stu-id="48c05-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="48c05-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="48c05-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="48c05-111">Indica a linguagem C++.</span><span class="sxs-lookup"><span data-stu-id="48c05-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="48c05-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="48c05-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="48c05-113">Indica a linguagem c#.</span><span class="sxs-lookup"><span data-stu-id="48c05-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="48c05-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="48c05-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="48c05-115">Indica o idioma básico.</span><span class="sxs-lookup"><span data-stu-id="48c05-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="48c05-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="48c05-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="48c05-117">Indica a linguagem Java.</span><span class="sxs-lookup"><span data-stu-id="48c05-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="48c05-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="48c05-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="48c05-119">Indica o idioma COBOL.</span><span class="sxs-lookup"><span data-stu-id="48c05-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="48c05-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="48c05-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="48c05-121">Indica o idioma Pascal.</span><span class="sxs-lookup"><span data-stu-id="48c05-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="48c05-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="48c05-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="48c05-123">Indica o código de assembly do Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="48c05-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="48c05-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="48c05-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="48c05-125">Indica a linguagem JScript.</span><span class="sxs-lookup"><span data-stu-id="48c05-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="48c05-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="48c05-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="48c05-127">Indica o idioma SMC.</span><span class="sxs-lookup"><span data-stu-id="48c05-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="48c05-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="48c05-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="48c05-129">Indica a linguagem C++ habilitada para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="48c05-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="48c05-130">Constantes de fornecedor de linguagem</span><span class="sxs-lookup"><span data-stu-id="48c05-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="48c05-131">A tabela a seguir mostra a linguagem de constantes de fornecedor, que representam os GUIDs que identificam os fornecedores de linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="48c05-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="48c05-132">Símbolo</span><span class="sxs-lookup"><span data-stu-id="48c05-132">Symbol</span></span>|<span data-ttu-id="48c05-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="48c05-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="48c05-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="48c05-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="48c05-135">Indica a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="48c05-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="48c05-136">Constantes de tipo de documento</span><span class="sxs-lookup"><span data-stu-id="48c05-136">Document Type Constants</span></span>  
 <span data-ttu-id="48c05-137">A tabela a seguir mostra as constantes de tipo, que representam os GUIDs que identificam os tipos de documento de documento.</span><span class="sxs-lookup"><span data-stu-id="48c05-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="48c05-138">Símbolo</span><span class="sxs-lookup"><span data-stu-id="48c05-138">Symbol</span></span>|<span data-ttu-id="48c05-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="48c05-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="48c05-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="48c05-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="48c05-141">Indica um documento de texto.</span><span class="sxs-lookup"><span data-stu-id="48c05-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="48c05-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="48c05-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="48c05-143">Indica um documento de texto não.</span><span class="sxs-lookup"><span data-stu-id="48c05-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48c05-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48c05-144">See Also</span></span>  
 [<span data-ttu-id="48c05-145">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="48c05-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
