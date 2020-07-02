---
title: Como empacotar um assembly .NET Framework para o COM
description: Empacotar um assembly .NET para COM. Reúna a lista de tipos que os aplicativos COM podem consumir, as instruções de controle de versão e implantação e a biblioteca de tipos.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 4963892419fd1caec4483123f820d62967a87dd6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620827"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="80fc8-104">Como empacotar um assembly .NET Framework para o COM</span><span class="sxs-lookup"><span data-stu-id="80fc8-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="80fc8-105">Desenvolvedores COM podem aproveitar as informações a seguir sobre os tipos gerenciados que pretendem incorporar em seus aplicativos:</span><span class="sxs-lookup"><span data-stu-id="80fc8-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="80fc8-106">Uma lista de tipos que aplicativos COM podem consumir</span><span class="sxs-lookup"><span data-stu-id="80fc8-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="80fc8-107">Alguns tipos gerenciados são visíveis para COM; alguns são visíveis, mas não instanciável; e alguns são visíveis e instanciáveis.</span><span class="sxs-lookup"><span data-stu-id="80fc8-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="80fc8-108">Um assembly pode incluir qualquer combinação de tipos invisíveis, visíveis, não instanciáveis e instanciáveis.</span><span class="sxs-lookup"><span data-stu-id="80fc8-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="80fc8-109">Para fins de integridade, identifique os tipos em um assembly que você pretende expor ao COM, especialmente quando esses tipos são um subconjunto dos tipos expostos ao .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="80fc8-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="80fc8-110">Para obter mais informações, consulte [Qualificando tipos do .NET para interoperação](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="80fc8-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="80fc8-111">Instruções de controle de versão</span><span class="sxs-lookup"><span data-stu-id="80fc8-111">Versioning instructions</span></span>

  <span data-ttu-id="80fc8-112">Classes gerenciadas que implementam a interface de classe (uma interface gerada por interoperabilidade COM) estão sujeitas a restrições de controle de versão.</span><span class="sxs-lookup"><span data-stu-id="80fc8-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="80fc8-113">Para obter diretrizes de como usar a interface de classe, consulte [Introdução à interface de classe](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="80fc8-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="80fc8-114">Instruções de implantação</span><span class="sxs-lookup"><span data-stu-id="80fc8-114">Deployment instructions</span></span>

  <span data-ttu-id="80fc8-115">Assemblies de nome forte que são assinados por um editor podem ser instalados no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="80fc8-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="80fc8-116">Assemblies não assinados devem ser instalados no computador do usuário como assemblies particulares.</span><span class="sxs-lookup"><span data-stu-id="80fc8-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="80fc8-117">Para obter mais informações, consulte [Considerações sobre segurança de assembly](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="80fc8-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="80fc8-118">Inclusão de biblioteca de tipos</span><span class="sxs-lookup"><span data-stu-id="80fc8-118">Type library inclusion</span></span>

  <span data-ttu-id="80fc8-119">A maioria dos tipos requerem uma biblioteca de tipos quando consumidos por um aplicativo COM.</span><span class="sxs-lookup"><span data-stu-id="80fc8-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="80fc8-120">Você pode gerar uma biblioteca de tipos ou fazer com que desenvolvedores COM executem essa tarefa.</span><span class="sxs-lookup"><span data-stu-id="80fc8-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="80fc8-121">O SDK do Windows fornece as seguintes opções para gerar uma biblioteca de tipos:</span><span class="sxs-lookup"><span data-stu-id="80fc8-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="80fc8-122">Exportador da Biblioteca de Tipos</span><span class="sxs-lookup"><span data-stu-id="80fc8-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="80fc8-123">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="80fc8-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="80fc8-124">Ferramenta de Registro de Assembly</span><span class="sxs-lookup"><span data-stu-id="80fc8-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="80fc8-125">Ferramenta de Instalação de Serviços .NET</span><span class="sxs-lookup"><span data-stu-id="80fc8-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="80fc8-126">Independentemente do mecanismo escolhido, somente os tipos públicos definidos no assembly que você fornecer são incluídos na biblioteca de tipos gerada.</span><span class="sxs-lookup"><span data-stu-id="80fc8-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="80fc8-127">Para obter instruções, consulte [Como inserir bibliotecas de tipos como recursos do Win32 em aplicativos baseados em .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="80fc8-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="80fc8-128">Exportador da Biblioteca de Tipos</span><span class="sxs-lookup"><span data-stu-id="80fc8-128">Type Library Exporter</span></span>

<span data-ttu-id="80fc8-129">O [Exportador da Biblioteca de Tipos (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) é uma ferramenta de linha de comando que converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="80fc8-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="80fc8-130">Quando as informações de tipo da classe estão disponíveis, os clientes COM podem criar uma instância da classe do .NET e chamar os métodos da instância, como se fosse um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="80fc8-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="80fc8-131">Tlbexp.exe converte um assembly inteiro de uma vez.</span><span class="sxs-lookup"><span data-stu-id="80fc8-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="80fc8-132">Não é possível usar Tlbexp.exe para gerar informações de tipo para um subconjunto dos tipos definidos em um assembly.</span><span class="sxs-lookup"><span data-stu-id="80fc8-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="80fc8-133">Classe TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="80fc8-133">TypeLibConverter Class</span></span>

<span data-ttu-id="80fc8-134">A classe <xref:System.Runtime.InteropServices.TypeLibConverter>, localizada no namespace **System.Runtime.Interop**, converte as classes e interfaces contidas em um assembly em uma biblioteca de tipos COM.</span><span class="sxs-lookup"><span data-stu-id="80fc8-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="80fc8-135">Essa API produz as mesmas informações que o Exportador da Biblioteca de Tipos, descrito na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="80fc8-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="80fc8-136">A **classe TypeLibConverter** implementa o <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="80fc8-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="80fc8-137">Ferramenta de Registro de Assembly</span><span class="sxs-lookup"><span data-stu-id="80fc8-137">Assembly Registration Tool</span></span>

<span data-ttu-id="80fc8-138">A [Ferramenta de Registro de Assembly (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) pode gerar e registrar uma biblioteca de tipos quando você aplica a opção **/tlb:**.</span><span class="sxs-lookup"><span data-stu-id="80fc8-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="80fc8-139">Clientes COM exigem que as bibliotecas de tipos sejam instaladas no Registro do Windows.</span><span class="sxs-lookup"><span data-stu-id="80fc8-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="80fc8-140">Sem essa opção, o Regasm.exe registra somente os tipos em um assembly, mas não a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="80fc8-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="80fc8-141">Registrar os tipos em um assembly e registrando a biblioteca de tipos são atividades distintas.</span><span class="sxs-lookup"><span data-stu-id="80fc8-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="80fc8-142">Ferramenta de Instalação de Serviços .NET</span><span class="sxs-lookup"><span data-stu-id="80fc8-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="80fc8-143">A [ferramenta de instalação de serviços .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adiciona classes gerenciadas para Serviços do Componente do Windows 2000 e combina várias tarefas em uma única ferramenta.</span><span class="sxs-lookup"><span data-stu-id="80fc8-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="80fc8-144">Além de carregar e registrar um assembly, Regsvcs.exe pode gerar, registrar e instalar a biblioteca de tipos em um aplicativo COM+ 1.0 existente.</span><span class="sxs-lookup"><span data-stu-id="80fc8-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="80fc8-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80fc8-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="80fc8-146">Expondo componentes do .NET Framework para COM</span><span class="sxs-lookup"><span data-stu-id="80fc8-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="80fc8-147">Qualificando tipos do .NET para interoperação</span><span class="sxs-lookup"><span data-stu-id="80fc8-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="80fc8-148">Introdução à interface de classe</span><span class="sxs-lookup"><span data-stu-id="80fc8-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="80fc8-149">Considerações de segurança do assembly</span><span class="sxs-lookup"><span data-stu-id="80fc8-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="80fc8-150">Tlbexp.exe (exportador de biblioteca de tipos)</span><span class="sxs-lookup"><span data-stu-id="80fc8-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="80fc8-151">Registrando assemblies com o COM</span><span class="sxs-lookup"><span data-stu-id="80fc8-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="80fc8-152">[Como inserir bibliotecas de tipo como recursos do Win32 em aplicativos](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="80fc8-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
