---
title: Realizando marshaling em dados com interoperabilidade COM
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 649936abfe149371445c77802bda2e72f558a41d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="e5ee1-102">Realizando marshaling em dados com interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="e5ee1-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="e5ee1-103">Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="e5ee1-104">O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="e5ee1-105">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] inclui as seguintes ferramentas de interoperabilidade COM:</span><span class="sxs-lookup"><span data-stu-id="e5ee1-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="e5ee1-106">[Importador de biblioteca de tipos (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="e5ee1-107">Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="e5ee1-108">[Digite o exportador da biblioteca (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="e5ee1-109">As seções a seguir links para tópicos que descrevem os processos para personalizar os wrappers de interoperabilidade quando você pode (ou deve) fornece o empacotador com informações de tipo adicionais.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5ee1-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e5ee1-110">In This Section</span></span>  
<span data-ttu-id="e5ee1-111">[Como: criar Wrappers manualmente](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="e5ee1-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="e5ee1-112">Descreve como criar um wrapper COM manualmente no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="e5ee1-113">Como: migrar código DCOM gerenciado para o WCF</span><span class="sxs-lookup"><span data-stu-id="e5ee1-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="e5ee1-114">Descreve como migrar o código gerenciado do DCOM para o WCF para a solução mais segura.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5ee1-115">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e5ee1-115">Related Sections</span></span>  
 <span data-ttu-id="e5ee1-116">[Tipos de dados COM](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-116">[COM Data Types](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-117">Fornece tipos de dados gerenciados e não gerenciados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="e5ee1-118">[Personalizando COM Callable Wrappers](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-119">Descreve como realizar marshaling explicitamente os tipos de dados usando o <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="e5ee1-120">[Personalizando RCWs (Runtime Callable Wrappers)](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-121">Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="e5ee1-122">[Interoperabilidade COM avançada](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-122">[Advanced COM Interoperability](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-123">Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="e5ee1-124">[Resumo da conversão de assemblies em bibliotecas de tipos](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-125">Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="e5ee1-126">[Resumo da conversão de bibliotecas de tipos em assemblies](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-127">Descreve o processo de conversão de importação de biblioteca de tipos em assembly.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="e5ee1-128">[Interoperação usando tipos genéricos](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="e5ee1-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="e5ee1-129">Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="e5ee1-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
