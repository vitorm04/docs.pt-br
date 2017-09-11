---
title: "Emitindo métodos e assemblies dinâmicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c28a5b71a93ea5159adc73316771d490dbe0db87
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="116c3-102">Emitindo métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="116c3-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="116c3-103">Esta seção descreve um conjunto de tipos gerenciados no namespace <xref:System.Reflection.Emit> que permite que um compilador ou ferramenta emita metadados e o MSIL (Microsoft Intermediate Language) no tempo de execução e, opcionalmente, gere um arquivo executável portátil (PE) no disco.</span><span class="sxs-lookup"><span data-stu-id="116c3-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="116c3-104">Mecanismos de script e compiladores são os principais usuários desse namespace.</span><span class="sxs-lookup"><span data-stu-id="116c3-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="116c3-105">Nesta seção, a funcionalidade fornecida pelo namespace <xref:System.Reflection.Emit> é conhecida como emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="116c3-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="116c3-106">A emissão de reflexão fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="116c3-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="116c3-107">Defina métodos globais leves no tempo de execução usando a classe <xref:System.Reflection.Emit.DynamicMethod> e execute-os usando delegados.</span><span class="sxs-lookup"><span data-stu-id="116c3-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="116c3-108">Defina os assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="116c3-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="116c3-109">Defina os assemblies no tempo de execução, execute-os, descarregue-os e permita que a coleta de lixo recupere seus recursos.</span><span class="sxs-lookup"><span data-stu-id="116c3-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="116c3-110">Defina módulos em novos assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="116c3-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="116c3-111">Defina os tipos de módulos no tempo de execução, crie instâncias desses tipos e invoque seus métodos.</span><span class="sxs-lookup"><span data-stu-id="116c3-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="116c3-112">Identifique as informações simbólicas para módulos definidos que podem ser usadas por ferramentas como depuradores e criadores de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="116c3-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="116c3-113">Além dos tipos gerenciados no namespace <xref:System.Reflection.Emit>, há interfaces de metadados não gerenciados que são descritos na documentação de referência de [Interfaces de Metadados](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="116c3-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="116c3-114">A emissão de reflexão gerenciada fornece verificação de erros semânticos mais potente e um nível mais alto de abstração de metadados que as interfaces de metadados não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="116c3-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="116c3-115">Outro recurso útil para trabalhar com metadados e MSIL é a documentação da CLI (Common Language Infrastructure), especialmente a “Partição II: definição e semântica de metadados” e a “Partição III: conjunto de instruções de CIL”.</span><span class="sxs-lookup"><span data-stu-id="116c3-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="116c3-116">A documentação está disponível online no [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) e no [site da Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="116c3-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="116c3-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="116c3-117">In This Section</span></span>  
 [<span data-ttu-id="116c3-118">Problemas de segurança na emissão de reflexão</span><span class="sxs-lookup"><span data-stu-id="116c3-118">Security Issues in Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 <span data-ttu-id="116c3-119">Descreve os problemas de segurança relacionados à criação de assemblies dinâmicos usando emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="116c3-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="116c3-120">Referência</span><span class="sxs-lookup"><span data-stu-id="116c3-120">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="116c3-121">Cataloga os códigos de instrução de MSIL, que você pode usar para criar corpos de método.</span><span class="sxs-lookup"><span data-stu-id="116c3-121">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="116c3-122">Contém classes gerenciadas usadas para emitir métodos, assemblies e tipos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="116c3-122">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="116c3-123">Descreve a classe <xref:System.Type>, que representa os tipos de reflexão gerenciada e emissão de reflexão, e qual é a chave para o uso dessas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="116c3-123">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="116c3-124">Contém classes gerenciadas usadas para explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="116c3-124">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="116c3-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="116c3-125">Related Sections</span></span>  
 [<span data-ttu-id="116c3-126">Reflexão</span><span class="sxs-lookup"><span data-stu-id="116c3-126">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="116c3-127">Explica como explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="116c3-127">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="116c3-128">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="116c3-128">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="116c3-129">Fornece uma visão geral dos assemblies no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="116c3-129">Provides an overview of assemblies in the .NET Framework.</span></span>

