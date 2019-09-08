---
title: Constantes (referência de API não gerenciada)
ms.date: 03/30/2017
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b91f2a749557f94a68f1929d649824719160d9ee
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786960"
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="94646-102">Constantes (referência de API não gerenciada)</span><span class="sxs-lookup"><span data-stu-id="94646-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="94646-103">Este tópico descreve as constantes tipo de idioma, fornecedor do idioma e tipo de documento que são definidas em CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="94646-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="94646-104">Constantes de tipo de linguagem</span><span class="sxs-lookup"><span data-stu-id="94646-104">Language Type Constants</span></span>  
 <span data-ttu-id="94646-105">A tabela a seguir mostra as constantes de tipo de linguagem, que representam GUIDs que identificam linguagens de programação.</span><span class="sxs-lookup"><span data-stu-id="94646-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="94646-106">Símbolo</span><span class="sxs-lookup"><span data-stu-id="94646-106">Symbol</span></span>|<span data-ttu-id="94646-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="94646-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94646-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="94646-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="94646-109">Indica a linguagem C.</span><span class="sxs-lookup"><span data-stu-id="94646-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="94646-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="94646-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="94646-111">Indica o C++ idioma.</span><span class="sxs-lookup"><span data-stu-id="94646-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="94646-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="94646-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="94646-113">Indica o C# idioma.</span><span class="sxs-lookup"><span data-stu-id="94646-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="94646-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="94646-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="94646-115">Indica a linguagem básica.</span><span class="sxs-lookup"><span data-stu-id="94646-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="94646-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="94646-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="94646-117">Indica a linguagem Java.</span><span class="sxs-lookup"><span data-stu-id="94646-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="94646-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="94646-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="94646-119">Indica o idioma COBOL.</span><span class="sxs-lookup"><span data-stu-id="94646-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="94646-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="94646-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="94646-121">Indica o idioma do Pascal.</span><span class="sxs-lookup"><span data-stu-id="94646-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="94646-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="94646-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="94646-123">Indica o código do assembly MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="94646-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="94646-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="94646-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="94646-125">Indica a linguagem JScript.</span><span class="sxs-lookup"><span data-stu-id="94646-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="94646-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="94646-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="94646-127">Indica a linguagem SMC.</span><span class="sxs-lookup"><span data-stu-id="94646-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="94646-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="94646-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="94646-129">Indica o C++ idioma habilitado para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94646-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="94646-130">Constantes de fornecedor de idioma</span><span class="sxs-lookup"><span data-stu-id="94646-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="94646-131">A tabela a seguir mostra as constantes de fornecedor de idioma, que representam GUIDs que identificam fornecedores de linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="94646-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="94646-132">Símbolo</span><span class="sxs-lookup"><span data-stu-id="94646-132">Symbol</span></span>|<span data-ttu-id="94646-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="94646-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94646-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="94646-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="94646-135">Indica a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="94646-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="94646-136">Constantes de tipo de documento</span><span class="sxs-lookup"><span data-stu-id="94646-136">Document Type Constants</span></span>  
 <span data-ttu-id="94646-137">A tabela a seguir mostra constantes de tipo de documento, que representam GUIDs que identificam tipos de documento.</span><span class="sxs-lookup"><span data-stu-id="94646-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="94646-138">Símbolo</span><span class="sxs-lookup"><span data-stu-id="94646-138">Symbol</span></span>|<span data-ttu-id="94646-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="94646-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="94646-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="94646-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="94646-141">Indica um documento de texto.</span><span class="sxs-lookup"><span data-stu-id="94646-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="94646-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="94646-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="94646-143">Indica um documento que não é de texto.</span><span class="sxs-lookup"><span data-stu-id="94646-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94646-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94646-144">See also</span></span>

- [<span data-ttu-id="94646-145">Referência de API não gerenciada</span><span class="sxs-lookup"><span data-stu-id="94646-145">Unmanaged API Reference</span></span>](index.md)
