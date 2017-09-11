---
title: Realizando marshaling em dados com interoperabilidade COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.assetid: 0bcdd7bf-5026-43eb-b08b-f03f90db9df9
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7e798f41f7c770fb0db0abf4a07e53cbaa6ccb40
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="41aa3-102">Realizando marshaling em dados com interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="41aa3-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="41aa3-103">Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM.</span><span class="sxs-lookup"><span data-stu-id="41aa3-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="41aa3-104">O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.</span><span class="sxs-lookup"><span data-stu-id="41aa3-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="41aa3-105">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] inclui as seguintes ferramentas de interoperabilidade COM:</span><span class="sxs-lookup"><span data-stu-id="41aa3-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="41aa3-106">[Importador de biblioteca de tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="41aa3-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="41aa3-107">Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="41aa3-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="41aa3-108">[Digite o exportador da biblioteca (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="41aa3-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="41aa3-109">Esta seção descreve os processos para personalizar os wrappers de interoperabilidade quando você pode (ou deve) fornecer informações de tipo adicionais ao marshaler.</span><span class="sxs-lookup"><span data-stu-id="41aa3-109">This section describes the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41aa3-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="41aa3-110">In This Section</span></span>  
 [<span data-ttu-id="41aa3-111">Tipos de dados COM</span><span class="sxs-lookup"><span data-stu-id="41aa3-111">COM Data Types</span></span>](http://msdn.microsoft.com/en-us/f93ae35d-a416-4218-8700-c8218cc90061)  
 <span data-ttu-id="41aa3-112">Fornece tipos de dados gerenciados e não gerenciados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="41aa3-112">Provides corresponding managed and unmanaged data types.</span></span>  
  
 [<span data-ttu-id="41aa3-113">Personalizando COM Callable Wrappers</span><span class="sxs-lookup"><span data-stu-id="41aa3-113">Customizing COM Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/825177d3-4b2c-4723-82be-ce6ca2c34ace)  
 <span data-ttu-id="41aa3-114">Descreve como realizar marshaling de tipos de dados explicitamente usando o atributo **MarshalAsAttribute** em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="41aa3-114">Describes how to explicitly marshal data types using the **MarshalAsAttribute** attribute at design time.</span></span>  
  
 [<span data-ttu-id="41aa3-115">Personalizando RCWs (Runtime Callable Wrappers)</span><span class="sxs-lookup"><span data-stu-id="41aa3-115">Customizing Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be)  
 <span data-ttu-id="41aa3-116">Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.</span><span class="sxs-lookup"><span data-stu-id="41aa3-116">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 [<span data-ttu-id="41aa3-117">Como: migrar código DCOM gerenciado para o WCF</span><span class="sxs-lookup"><span data-stu-id="41aa3-117">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="41aa3-118">Descreve como migrar o código DCOM gerenciado para WCF para a solução mais segura.</span><span class="sxs-lookup"><span data-stu-id="41aa3-118">Described how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41aa3-119">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="41aa3-119">Related Sections</span></span>  
 [<span data-ttu-id="41aa3-120">Interoperabilidade COM avançada</span><span class="sxs-lookup"><span data-stu-id="41aa3-120">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 <span data-ttu-id="41aa3-121">Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41aa3-121">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 [<span data-ttu-id="41aa3-122">Resumo da conversão de assemblies em bibliotecas de tipos</span><span class="sxs-lookup"><span data-stu-id="41aa3-122">Assembly to Type Library Conversion Summary</span></span>](http://msdn.microsoft.com/en-us/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 <span data-ttu-id="41aa3-123">Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="41aa3-123">Describes the assembly to type library export conversion process.</span></span>  
  
 [<span data-ttu-id="41aa3-124">Resumo da conversão de bibliotecas de tipos em assemblies</span><span class="sxs-lookup"><span data-stu-id="41aa3-124">Type Library to Assembly Conversion Summary</span></span>](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 <span data-ttu-id="41aa3-125">Descreve o processo de conversão de importação de biblioteca de tipos em assembly.</span><span class="sxs-lookup"><span data-stu-id="41aa3-125">Describes the type library to assembly import conversion process.</span></span>  
  
 [<span data-ttu-id="41aa3-126">Interoperação usando tipos genéricos</span><span class="sxs-lookup"><span data-stu-id="41aa3-126">Interoperating Using Generic Types</span></span>](http://msdn.microsoft.com/en-us/26b88e03-085b-4b53-94ba-a5a9c709ce58)  
 <span data-ttu-id="41aa3-127">Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="41aa3-127">Describes which actions are supported when using generic types for COM interoperability.</span></span>

