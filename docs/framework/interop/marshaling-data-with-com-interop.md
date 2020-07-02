---
title: Realizando marshaling em dados com interoperabilidade COM
description: Consulte os artigos que abordam o marshaling de dados com interoperabilidade COM. As ferramentas Tlbimp.exe e Tlbexp.exe são convertidas entre uma biblioteca de tipos COM e um assembly de interoperabilidade.
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
ms.openlocfilehash: eedfb60a75e2fe5fafdaa786dbb54adddf28400e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621503"
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="8ad7e-104">Realizando marshaling em dados com interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="8ad7e-104">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="8ad7e-105">Interoperabilidade COM dá suporte ao uso de objetos COM por código gerenciado e à exposição de objetos gerenciados para COM.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-105">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="8ad7e-106">O suporte a marshaling dos dados de e para o COM é abrangente e quase sempre proporciona o comportamento de marshaling correto.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-106">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="8ad7e-107">O SDK do Windows inclui as seguintes ferramentas de interoperabilidade COM:</span><span class="sxs-lookup"><span data-stu-id="8ad7e-107">The Windows SDK includes the following COM interop tools:</span></span>  
  
- <span data-ttu-id="8ad7e-108">[Importador de biblioteca de tipos (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), que converte uma biblioteca de tipos COM para um assembly de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-108">[Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="8ad7e-109">Desse assembly, o serviço de marshaling de interoperabilidade gera wrappers que realizam marshaling entre memória gerenciada e não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-109">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
- <span data-ttu-id="8ad7e-110">[Digite o exportador da biblioteca (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), que produz uma biblioteca de tipos COM de um assembly e gera um wrapper que realiza marshaling durante as chamadas de método.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-110">[Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="8ad7e-111">As seções a seguir são vinculadas a tópicos que descrevem os processos para personalizar os wrappers de interoperabilidade quando você pode (ou precisa) fornecer informações de tipo adicionais ao marshaler.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-111">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8ad7e-112">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8ad7e-112">In This Section</span></span>  
<span data-ttu-id="8ad7e-113">[Como criar wrappers manualmente](how-to-create-wrappers-manually.md) Descreve como criar um wrapper COM manualmente no código-fonte gerenciado.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-113">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) Describes how to create a COM wrapper manually in managed source code.</span></span>

 [<span data-ttu-id="8ad7e-114">Como: Migrar código DCOM gerenciado para o WCF</span><span class="sxs-lookup"><span data-stu-id="8ad7e-114">How to: Migrate Managed-Code DCOM to WCF</span></span>](how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="8ad7e-115">Descreve como migrar o código DCOM gerenciado para o WCF para obter a solução mais segura possível.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-115">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ad7e-116">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8ad7e-116">Related Sections</span></span>  
 <span data-ttu-id="8ad7e-117">[Tipos de dados COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-117">[COM Data Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sak564ww(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-118">Fornece tipos de dados gerenciados e não gerenciados correspondentes.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-118">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="8ad7e-119">[Personalizando COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-119">[Customizing COM Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3bwc828w(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-120">Descreve como realizar marshaling nos tipos de dados explicitamente usando o atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-120">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="8ad7e-121">[Personalizando RCWs (Runtime Callable Wrappers)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-121">[Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-122">Descreve como ajustar o comportamento de marshaling de tipos em um assembly de interoperabilidade e como definir tipos COM manualmente.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-122">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="8ad7e-123">[Interoperabilidade COM avançada](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-123">[Advanced COM Interoperability](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-124">Fornece links para obter mais informações sobre como incorporar componentes COM no aplicativo do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-124">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8ad7e-125">[Resumo da conversão de assemblies em bibliotecas de tipos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-125">[Assembly to Type Library Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xk1120c3(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-126">Descreve o processo de conversão de exportação de assembly em biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-126">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="8ad7e-127">[Resumo da conversão de bibliotecas de tipos em assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-127">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-128">Descreve o processo de conversão de importação de biblioteca de tipos em assembly.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-128">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="8ad7e-129">[Interoperação usando tipos genéricos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ad7e-129">[Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100))</span></span>  
 <span data-ttu-id="8ad7e-130">Descreve quais ações têm suporte ao usar tipos genéricos para interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="8ad7e-130">Describes which actions are supported when using generic types for COM interoperability.</span></span>
