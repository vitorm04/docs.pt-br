---
title: Emitindo métodos e assemblies dinâmicos
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 527da43807a0dbba8f5365c92f566053f10d49f5
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2018
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="f32a8-102">Emitindo métodos e assemblies dinâmicos</span><span class="sxs-lookup"><span data-stu-id="f32a8-102">Emitting Dynamic Methods and Assemblies</span></span>
<span data-ttu-id="f32a8-103">Esta seção descreve um conjunto de tipos gerenciados no namespace <xref:System.Reflection.Emit> que permite que um compilador ou ferramenta emita metadados e o MSIL (Microsoft Intermediate Language) no tempo de execução e, opcionalmente, gere um arquivo executável portátil (PE) no disco.</span><span class="sxs-lookup"><span data-stu-id="f32a8-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="f32a8-104">Mecanismos de script e compiladores são os principais usuários desse namespace.</span><span class="sxs-lookup"><span data-stu-id="f32a8-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="f32a8-105">Nesta seção, a funcionalidade fornecida pelo namespace <xref:System.Reflection.Emit> é conhecida como emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="f32a8-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
 <span data-ttu-id="f32a8-106">A emissão de reflexão fornece os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="f32a8-106">Reflection emit provides the following capabilities:</span></span>  
  
-   <span data-ttu-id="f32a8-107">Defina métodos globais leves no tempo de execução usando a classe <xref:System.Reflection.Emit.DynamicMethod> e execute-os usando delegados.</span><span class="sxs-lookup"><span data-stu-id="f32a8-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
-   <span data-ttu-id="f32a8-108">Defina os assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="f32a8-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="f32a8-109">Defina os assemblies no tempo de execução, execute-os, descarregue-os e permita que a coleta de lixo recupere seus recursos.</span><span class="sxs-lookup"><span data-stu-id="f32a8-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
-   <span data-ttu-id="f32a8-110">Defina módulos em novos assemblies no tempo de execução e, em seguida, execute-os e/ou salve-os em disco.</span><span class="sxs-lookup"><span data-stu-id="f32a8-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
-   <span data-ttu-id="f32a8-111">Defina os tipos de módulos no tempo de execução, crie instâncias desses tipos e invoque seus métodos.</span><span class="sxs-lookup"><span data-stu-id="f32a8-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
-   <span data-ttu-id="f32a8-112">Identifique as informações simbólicas para módulos definidos que podem ser usadas por ferramentas como depuradores e criadores de perfil de código.</span><span class="sxs-lookup"><span data-stu-id="f32a8-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
 <span data-ttu-id="f32a8-113">Além dos tipos gerenciados no namespace <xref:System.Reflection.Emit>, há interfaces de metadados não gerenciados que são descritos na documentação de referência de [Interfaces de Metadados](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="f32a8-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="f32a8-114">A emissão de reflexão gerenciada fornece verificação de erros semânticos mais potente e um nível mais alto de abstração de metadados que as interfaces de metadados não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="f32a8-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
 <span data-ttu-id="f32a8-115">Outro recurso útil para trabalhar com metadados e MSIL é a documentação da CLI (Common Language Infrastructure), especialmente a “Partição II: definição e semântica de metadados” e a “Partição III: conjunto de instruções de CIL”.</span><span class="sxs-lookup"><span data-stu-id="f32a8-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="f32a8-116">A documentação está disponível online no [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) e no [site da Ecma](http://go.microsoft.com/fwlink/?LinkId=116487).</span><span class="sxs-lookup"><span data-stu-id="f32a8-116">The documentation is available online on [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](http://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f32a8-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f32a8-117">In This Section</span></span>
  
[<span data-ttu-id="f32a8-118">Problemas de segurança na emissão de reflexão</span><span class="sxs-lookup"><span data-stu-id="f32a8-118">Security issues in reflection emit</span></span>](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
<span data-ttu-id="f32a8-119">Descreve os problemas de segurança relacionados à criação de assemblies dinâmicos usando emissão de reflexão.</span><span class="sxs-lookup"><span data-stu-id="f32a8-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="f32a8-120">[Como definir e executar métodos dinâmicos](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="f32a8-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="f32a8-121">Mostra como executar um método dinâmico simples e um método dinâmico vinculado a uma instância de uma classe.</span><span class="sxs-lookup"><span data-stu-id="f32a8-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="f32a8-122">[Como definir um tipo genérico com a emissão de reflexão](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="f32a8-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="f32a8-123">Mostra como criar um tipo genérico simples com dois parâmetros de tipo, como aplicar restrições especiais, de classe e de interface aos parâmetros de tipo e como criar membros que usam os parâmetros de tipo da classe como tipos de parâmetro e tipos de retorno.</span><span class="sxs-lookup"><span data-stu-id="f32a8-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="f32a8-124">[Como definir um método genérico com a emissão de reflexão](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="f32a8-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="f32a8-125">Mostra como criar, emitir e invocar um método genérico simples.</span><span class="sxs-lookup"><span data-stu-id="f32a8-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="f32a8-126">[Assemblies de coleção para geração de tipos dinâmicos](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="f32a8-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="f32a8-127">Apresenta os assemblies de coleção, que são assemblies dinâmicos que podem ser descarregados sem descarregar o domínio do aplicativo no qual eles foram criados.</span><span class="sxs-lookup"><span data-stu-id="f32a8-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="f32a8-128">Referência</span><span class="sxs-lookup"><span data-stu-id="f32a8-128">Reference</span></span>  
 <xref:System.Reflection.Emit.OpCodes>  
 <span data-ttu-id="f32a8-129">Cataloga os códigos de instrução de MSIL, que você pode usar para criar corpos de método.</span><span class="sxs-lookup"><span data-stu-id="f32a8-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
 <xref:System.Reflection.Emit>  
 <span data-ttu-id="f32a8-130">Contém classes gerenciadas usadas para emitir métodos, assemblies e tipos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="f32a8-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
 <xref:System.Type>  
 <span data-ttu-id="f32a8-131">Descreve a classe <xref:System.Type>, que representa os tipos de reflexão gerenciada e emissão de reflexão, e qual é a chave para o uso dessas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="f32a8-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
 <xref:System.Reflection>  
 <span data-ttu-id="f32a8-132">Contém classes gerenciadas usadas para explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f32a8-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f32a8-133">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f32a8-133">Related Sections</span></span>  
 [<span data-ttu-id="f32a8-134">Reflexão</span><span class="sxs-lookup"><span data-stu-id="f32a8-134">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="f32a8-135">Explica como explorar os metadados e o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f32a8-135">Explains how to explore metadata and managed code.</span></span>  
  
 [<span data-ttu-id="f32a8-136">Assemblies no Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="f32a8-136">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="f32a8-137">Fornece uma visão geral dos assemblies em implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="f32a8-137">Provides an overview of assemblies in .NET implementations.</span></span>
