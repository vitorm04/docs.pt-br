---
title: Interoperabilidade COM (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, COM interop
- COM interop [Visual Basic], in Visual Basic
ms.assetid: 3ffd1bdf-1b8d-47f5-87eb-75b659f64294
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2c418855cd2e79c31301705706ff1b98f119a97
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="com-interop-visual-basic"></a><span data-ttu-id="ef6fb-102">Interoperabilidade COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef6fb-102">COM Interop (Visual Basic)</span></span>
<span data-ttu-id="ef6fb-103">O COM (Component Object Model) permite que um objeto exponha sua funcionalidade a outros componentes e aplicativos host.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-103">The Component Object Model (COM) allows an object to expose its functionality to other components and to host applications.</span></span> <span data-ttu-id="ef6fb-104">Atualmente, a maioria dos softwares incluem objetos COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-104">Most of today's software includes COM objects.</span></span> <span data-ttu-id="ef6fb-105">Embora os assemblies .NET sejam a melhor opção para novos aplicativos, algumas vezes será preciso empregar objetos COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-105">Although .NET assemblies are the best choice for new applications, you may at times need to employ COM objects.</span></span> <span data-ttu-id="ef6fb-106">Esta seção aborda alguns dos problemas associados ao criar e usar objetos COM o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-106">This section covers some of the issues associated with creating and using COM objects with Visual Basic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef6fb-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ef6fb-107">In This Section</span></span>  
 [<span data-ttu-id="ef6fb-108">Introdução à Interoperabilidade COM</span><span class="sxs-lookup"><span data-stu-id="ef6fb-108">Introduction to COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/introduction-to-com-interop.md)  
 <span data-ttu-id="ef6fb-109">Fornece uma visão geral da interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-109">Provides an overview of COM interoperability.</span></span>  
  
 [<span data-ttu-id="ef6fb-110">Como referenciar objetos COM no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef6fb-110">How to: Reference COM Objects from Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-reference-com-objects.md)  
 <span data-ttu-id="ef6fb-111">Aborda como adicionar referências a objetos COM que têm bibliotecas de tipos.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-111">Covers how to add references to COM objects that have type libraries.</span></span>  
  
 [<span data-ttu-id="ef6fb-112">Como trabalhar com controles ActiveX</span><span class="sxs-lookup"><span data-stu-id="ef6fb-112">How to: Work with ActiveX Controls</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-work-with-activex-controls.md)  
 <span data-ttu-id="ef6fb-113">Demonstra como usar controles ActiveX existente para adicionar recursos para ferramentas do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-113">Demonstrates how to use existing ActiveX controls to add features to the Visual Studio Toolbox.</span></span>  
  
 [<span data-ttu-id="ef6fb-114">Instruções passo a passo: chamando APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="ef6fb-114">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 <span data-ttu-id="ef6fb-115">Orienta o processo de chamada às APIs que fazem parte do sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-115">Steps you through the process of calling the APIs that are part of the Windows operating system.</span></span>  
  
 [<span data-ttu-id="ef6fb-116">Como chamar APIs do Windows</span><span class="sxs-lookup"><span data-stu-id="ef6fb-116">How to: Call Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-windows-apis.md)  
 <span data-ttu-id="ef6fb-117">Demonstra como definir e chamar a função `MessageBox` em User32.dll.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-117">Demonstrates how to define and call the `MessageBox` function in User32.dll.</span></span>  
  
 [<span data-ttu-id="ef6fb-118">Como chamar uma função do Windows que use tipos não assinados</span><span class="sxs-lookup"><span data-stu-id="ef6fb-118">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 <span data-ttu-id="ef6fb-119">Demonstra como chamar uma função do Windows que tem um parâmetro de tipo não assinado.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-119">Demonstrates how to call a Windows function that has a parameter of an unsigned type.</span></span>  
  
 [<span data-ttu-id="ef6fb-120">Instruções passo a passo: criando objetos COM com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef6fb-120">Walkthrough: Creating COM Objects with Visual Basic</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-creating-com-objects.md)  
 <span data-ttu-id="ef6fb-121">Orienta o processo de criação de objetos COM com e sem o modelo de classe COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-121">Steps you through the process of creating COM objects with and without the COM class template.</span></span>  
  
 [<span data-ttu-id="ef6fb-122">Solução de problemas de Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ef6fb-122">Troubleshooting Interoperability</span></span>](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 <span data-ttu-id="ef6fb-123">Aborda alguns dos problemas que você pode encontrar ao usar o COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-123">Covers some of the problems you may encounter when using COM.</span></span>  
  
 [<span data-ttu-id="ef6fb-124">Interoperabilidade COM em Aplicativos .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ef6fb-124">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 <span data-ttu-id="ef6fb-125">Fornece uma visão geral de como usar objetos COM e objetos .NET Framework no mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-125">Provides an overview of how to use COM objects and .NET Framework objects in the same application.</span></span>  
  
 [<span data-ttu-id="ef6fb-126">Instruções passo a passo: implementando a herança com objetos COM</span><span class="sxs-lookup"><span data-stu-id="ef6fb-126">Walkthrough: Implementing Inheritance with COM Objects</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 <span data-ttu-id="ef6fb-127">Descreve como usar objetos COM existentes como base para novos objetos.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-127">Describes using existing COM objects as the basis for new objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef6fb-128">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ef6fb-128">Related Sections</span></span>  
 [<span data-ttu-id="ef6fb-129">Interoperação com código não gerenciado</span><span class="sxs-lookup"><span data-stu-id="ef6fb-129">Interoperating with Unmanaged Code</span></span>](../../../framework/interop/index.md)  
 <span data-ttu-id="ef6fb-130">Descreve os serviços de interoperabilidade fornecidos pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-130">Describes interoperability services provided by the common language runtime.</span></span>  
  
 [<span data-ttu-id="ef6fb-131">Expondo componentes do COM ao .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ef6fb-131">Exposing COM Components to the .NET Framework</span></span>](http://msdn.microsoft.com/library/e78b14f1-e487-43cd-9c6d-1a07483f1730)  
 <span data-ttu-id="ef6fb-132">Descreve o processo de chamada de tipos COM por meio da interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-132">Describes the process of calling COM types through COM interop.</span></span>  
  
 [<span data-ttu-id="ef6fb-133">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="ef6fb-133">Exposing .NET Framework Components to COM</span></span>](http://msdn.microsoft.com/library/e42a65f7-1e61-411f-b09a-aca1bbce24c6)  
 <span data-ttu-id="ef6fb-134">Descreve a preparação e o uso de tipos gerenciados do COM.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-134">Describes the preparation and use of managed types from COM.</span></span>  
  
 [<span data-ttu-id="ef6fb-135">Aplicando atributos de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="ef6fb-135">Applying Interop Attributes</span></span>](../../../framework/interop/applying-interop-attributes.md)  
 <span data-ttu-id="ef6fb-136">Aborda os atributos que você pode usar ao trabalhar com código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ef6fb-136">Covers attributes you can use when working with unmanaged code.</span></span>
