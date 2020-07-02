---
title: Interoperação com código não gerenciado
description: Examine a interoperação com código não gerenciado. O CLR oculta de clientes e servidores como os modelos de objeto de componentes .NET e código não gerenciado são diferentes.
ms.date: 01/17/2018
helpviewer_keywords:
- unmanaged code, interoperation
- managed code, interoperation with unmanaged code
- .NET Framework, interoperation with unmanaged code
- unmanaged code
- interoperation with unmanaged code
- interoperation with unmanaged code, about interoperation
- components [.NET Framework], interoperation with unmanaged code
ms.assetid: ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258
ms.openlocfilehash: 1cebd75907fd202715cb337593186d248107bdbb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621867"
---
# <a name="interoperating-with-unmanaged-code"></a><span data-ttu-id="e9d2b-104">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="e9d2b-104">Interoperating with unmanaged code</span></span>

<span data-ttu-id="e9d2b-105">O .NET Framework promove a interação com componentes COM, serviços COM+, bibliotecas de tipos externas e muitos serviços do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-105">The .NET Framework promotes interaction with COM components, COM+ services, external type libraries, and many operating system services.</span></span> <span data-ttu-id="e9d2b-106">Tipos de dados, assinaturas de método e mecanismos de tratamento de erros variam entre modelos de objetos gerenciados e não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-106">Data types, method signatures, and error-handling mechanisms vary between managed and unmanaged object models.</span></span> <span data-ttu-id="e9d2b-107">Para simplificar a interoperação entre componentes do .NET Framework e o código não gerenciado e para facilitar o caminho de migração, o Common Language Runtime oculta de clientes e servidores as diferenças entre esses modelos de objeto.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-107">To simplify interoperation between .NET Framework components and unmanaged code and to ease the migration path, the common language runtime conceals from both clients and servers the differences in these object models.</span></span>

<span data-ttu-id="e9d2b-108">O código que é executado sob o controle de runtime é chamado de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-108">Code that executes under the control of the runtime is called managed code.</span></span> <span data-ttu-id="e9d2b-109">Em contraste, o código executado fora do runtime é chamado de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-109">Conversely, code that runs outside the runtime is called unmanaged code.</span></span> <span data-ttu-id="e9d2b-110">Componentes COM, interfaces ActiveX e funções da API do Windows são exemplos de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-110">COM components, ActiveX interfaces, and Windows API functions are examples of unmanaged code.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e9d2b-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e9d2b-111">In this section</span></span>

[<span data-ttu-id="e9d2b-112">Expondo componentes do COM para o .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e9d2b-112">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)  
<span data-ttu-id="e9d2b-113">Descreve como usar componentes COM de aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-113">Describes how to use COM components from .NET Framework applications.</span></span>

[<span data-ttu-id="e9d2b-114">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="e9d2b-114">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
<span data-ttu-id="e9d2b-115">Descreve como usar componentes do .NET Framework de aplicativos COM.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-115">Describes how to use .NET Framework components from COM applications.</span></span>

[<span data-ttu-id="e9d2b-116">Consumindo funções de DLL não gerenciadas</span><span class="sxs-lookup"><span data-stu-id="e9d2b-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
<span data-ttu-id="e9d2b-117">Descreve como chamar funções de DLL não gerenciadas usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>

[<span data-ttu-id="e9d2b-118">Realizando marshaling de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="e9d2b-118">Interop Marshaling</span></span>](interop-marshaling.md)  
<span data-ttu-id="e9d2b-119">Descreve o marshaling para invocação de plataforma e interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-119">Describes marshaling for COM interop and platform invoke.</span></span>

[<span data-ttu-id="e9d2b-120">Como: Mapear HRESULTs e exceções</span><span class="sxs-lookup"><span data-stu-id="e9d2b-120">How to: Map HRESULTs and Exceptions</span></span>](how-to-map-hresults-and-exceptions.md)  
<span data-ttu-id="e9d2b-121">Descreve o mapeamento entre exceções e HRESULTs.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-121">Describes the mapping between exceptions and HRESULTs.</span></span>

[<span data-ttu-id="e9d2b-122">Equivalência de tipo e tipos de interoperabilidade inseridos</span><span class="sxs-lookup"><span data-stu-id="e9d2b-122">Type Equivalence and Embedded Interop Types</span></span>](type-equivalence-and-embedded-interop-types.md)  
<span data-ttu-id="e9d2b-123">Descreve como as informações de tipo para tipos COM são inseridas em assemblies e como o Common Language Runtime determina a equivalência de tipos COM inseridos.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-123">Describes how type information for COM types is embedded in assemblies, and how the common language runtime determines the equivalence of embedded COM types.</span></span>

[<span data-ttu-id="e9d2b-124">Como: Gerar assemblies de interoperabilidade primários usando Tlbimp.exe</span><span class="sxs-lookup"><span data-stu-id="e9d2b-124">How to: Generate Primary Interop Assemblies Using Tlbimp.exe</span></span>](how-to-generate-primary-interop-assemblies-using-tlbimp-exe.md)  
<span data-ttu-id="e9d2b-125">Descreve como gerar assemblies de interoperabilidade primários usando *Tlbimp.exe* (Importador da Biblioteca de Tipos).</span><span class="sxs-lookup"><span data-stu-id="e9d2b-125">Describes how to produce primary interop assemblies using *Tlbimp.exe* (Type Library Importer).</span></span>

[<span data-ttu-id="e9d2b-126">Como: Registrar assemblies de interoperabilidade primários</span><span class="sxs-lookup"><span data-stu-id="e9d2b-126">How to: Register Primary Interop Assemblies</span></span>](how-to-register-primary-interop-assemblies.md)  
<span data-ttu-id="e9d2b-127">Descreve como registrar os assemblies de interoperabilidade primários antes de referenciá-los em seus projetos.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-127">Describes how to register the primary interop assemblies before you can reference them in your projects.</span></span>

[<span data-ttu-id="e9d2b-128">Interoperabilidade COM sem registro</span><span class="sxs-lookup"><span data-stu-id="e9d2b-128">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)  
<span data-ttu-id="e9d2b-129">Descreve como a interoperabilidade COM pode ativar componentes sem usar o Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-129">Describes how COM interop can activate components without using the Windows registry.</span></span>

[<span data-ttu-id="e9d2b-130">Como: Configurar componentes COM baseados no .NET Framework para ativação sem registro</span><span class="sxs-lookup"><span data-stu-id="e9d2b-130">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](configure-net-framework-based-com-components-for-reg.md)  
<span data-ttu-id="e9d2b-131">Descreve como criar um manifesto do aplicativo e como criar e inserir um manifesto do componente.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-131">Describes how to create an application manifest and how to create and embed a component manifest.</span></span>

## <a name="related-sections"></a><span data-ttu-id="e9d2b-132">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e9d2b-132">Related sections</span></span>

[<span data-ttu-id="e9d2b-133">Wrappers COM</span><span class="sxs-lookup"><span data-stu-id="e9d2b-133">COM Wrappers</span></span>](../../standard/native-interop/com-wrappers.md)  
<span data-ttu-id="e9d2b-134">Descreve os wrappers fornecidos pela interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="e9d2b-134">Describes the wrappers provided by COM interop.</span></span>
