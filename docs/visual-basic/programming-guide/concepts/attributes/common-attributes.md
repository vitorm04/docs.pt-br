---
title: Atributos comuns (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9adb5cb378701c8d06a3fa28bad44dc857026b5a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="ef63b-102">Atributos comuns (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef63b-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="ef63b-103">Este tópico descreve os atributos que são mais comumente usados nos programas em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef63b-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="ef63b-104">Atributos globais</span><span class="sxs-lookup"><span data-stu-id="ef63b-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="ef63b-105">Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="ef63b-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="ef63b-106">Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="ef63b-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="ef63b-107">Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="ef63b-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="ef63b-108">Atributos do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef63b-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <span data-ttu-id="ef63b-109"><a name="Global"></a>Atributos globais</span><span class="sxs-lookup"><span data-stu-id="ef63b-109"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="ef63b-110">A maioria dos atributos são aplicados aos elementos de idioma específico, como classes ou métodos; No entanto, alguns atributos são globais — eles se aplicam a um conjunto inteiro ou módulo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="ef63b-111">Por exemplo, o <xref:System.Reflection.AssemblyVersionAttribute>atributo pode ser usado para incorporar informações de versão em um assembly, como este:</xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="ef63b-112">Atributos globais aparecem no código-fonte após qualquer nível superior`Imports` instruções e antes de quaisquer declarações de namespace, módulo ou tipo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-112">Global attributes appear in the source code after any top-level`Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="ef63b-113">Atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser criados em uma passagem de compilação única.</span><span class="sxs-lookup"><span data-stu-id="ef63b-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="ef63b-114">Para projetos do Visual Basic, os atributos globais geralmente são colocados no arquivo AssemblyInfo VB (o arquivo é criado automaticamente quando você cria um projeto no Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="ef63b-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="ef63b-115">Atributos de assembly são valores que fornecem informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="ef63b-116">Elas se encaixam nas seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="ef63b-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="ef63b-117">Atributos de identidade de assembly</span><span class="sxs-lookup"><span data-stu-id="ef63b-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="ef63b-118">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="ef63b-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="ef63b-119">Atributos do manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="ef63b-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="ef63b-120">Atributos de identidade de assembly</span><span class="sxs-lookup"><span data-stu-id="ef63b-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="ef63b-121">Três atributos (com um nome forte, se aplicável) determinam a identidade de um conjunto: nome, versão e cultura.</span><span class="sxs-lookup"><span data-stu-id="ef63b-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="ef63b-122">Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código.</span><span class="sxs-lookup"><span data-stu-id="ef63b-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="ef63b-123">Você pode definir a versão e cultura usando atributos de um assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="ef63b-124">No entanto, o valor do nome é definido pelo compilador, a IDE do Visual Studio no [caixa de diálogo de informações do Assembly](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), ou o Assembly Linker (Al.exe) quando o assembly é criado, com base em arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](https://docs.microsoft.com/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="ef63b-125">O <xref:System.Reflection.AssemblyFlagsAttribute>atributo especifica se várias cópias do conjunto podem coexistir.</xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="ef63b-126">A tabela a seguir mostra os atributos de identidade.</span><span class="sxs-lookup"><span data-stu-id="ef63b-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="ef63b-127">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-127">Attribute</span></span>|<span data-ttu-id="ef63b-128">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ef63b-128">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="ef63b-129"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="ef63b-129"><xref:System.Reflection.AssemblyName></span></span>|<span data-ttu-id="ef63b-130">Descreve totalmente a identidade de um assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-130">Fully describes the identity of an assembly.</span></span>|  
|<span data-ttu-id="ef63b-131"><xref:System.Reflection.AssemblyVersionAttribute></xref:System.Reflection.AssemblyVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-131"><xref:System.Reflection.AssemblyVersionAttribute></span></span>|<span data-ttu-id="ef63b-132">Especifica a versão de um assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-132">Specifies the version of an assembly.</span></span>|  
|<span data-ttu-id="ef63b-133"><xref:System.Reflection.AssemblyCultureAttribute></xref:System.Reflection.AssemblyCultureAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-133"><xref:System.Reflection.AssemblyCultureAttribute></span></span>|<span data-ttu-id="ef63b-134">Especifica a qual cultura o assembly dá suporte.</span><span class="sxs-lookup"><span data-stu-id="ef63b-134">Specifies which culture the assembly supports.</span></span>|  
|<span data-ttu-id="ef63b-135"><xref:System.Reflection.AssemblyFlagsAttribute></xref:System.Reflection.AssemblyFlagsAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-135"><xref:System.Reflection.AssemblyFlagsAttribute></span></span>|<span data-ttu-id="ef63b-136">Especifica se um assembly oferece suporte à execução lado a lado no mesmo computador, no mesmo processo, ou no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-136">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="ef63b-137">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="ef63b-137">Informational Attributes</span></span>  
 <span data-ttu-id="ef63b-138">Você pode usar atributos informativos para fornecer informações de produto para um assembly ou empresas adicionais.</span><span class="sxs-lookup"><span data-stu-id="ef63b-138">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="ef63b-139">A tabela a seguir mostra os atributos informativos definidos no <xref:System.Reflection?displayProperty=fullName>namespace.</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ef63b-139">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="ef63b-140">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-140">Attribute</span></span>|<span data-ttu-id="ef63b-141">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ef63b-141">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="ef63b-142"><xref:System.Reflection.AssemblyProductAttribute></xref:System.Reflection.AssemblyProductAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-142"><xref:System.Reflection.AssemblyProductAttribute></span></span>|<span data-ttu-id="ef63b-143">Define um atributo personalizado que especifica um nome de produto para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-143">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-144"><xref:System.Reflection.AssemblyTrademarkAttribute></xref:System.Reflection.AssemblyTrademarkAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-144"><xref:System.Reflection.AssemblyTrademarkAttribute></span></span>|<span data-ttu-id="ef63b-145">Define um atributo personalizado que especifica uma marca comercial para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-145">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></xref:System.Reflection.AssemblyInformationalVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-146"><xref:System.Reflection.AssemblyInformationalVersionAttribute></span></span>|<span data-ttu-id="ef63b-147">Define um atributo personalizado que especifica uma versão informacional para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-147">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-148"><xref:System.Reflection.AssemblyCompanyAttribute></xref:System.Reflection.AssemblyCompanyAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-148"><xref:System.Reflection.AssemblyCompanyAttribute></span></span>|<span data-ttu-id="ef63b-149">Define um atributo personalizado que especifica um nome de empresa para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-149">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-150"><xref:System.Reflection.AssemblyCopyrightAttribute></xref:System.Reflection.AssemblyCopyrightAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-150"><xref:System.Reflection.AssemblyCopyrightAttribute></span></span>|<span data-ttu-id="ef63b-151">Define um atributo personalizado que especifica um copyright para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-151">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-152"><xref:System.Reflection.AssemblyFileVersionAttribute></xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-152"><xref:System.Reflection.AssemblyFileVersionAttribute></span></span>|<span data-ttu-id="ef63b-153">Instrui o compilador a usar um número de versão específico para o recurso de versão de arquivo do Win32.</span><span class="sxs-lookup"><span data-stu-id="ef63b-153">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<span data-ttu-id="ef63b-154"><xref:System.CLSCompliantAttribute></xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-154"><xref:System.CLSCompliantAttribute></span></span>|<span data-ttu-id="ef63b-155">Indica se o assembly é compatível com o Common Language Specification (CLS).</span><span class="sxs-lookup"><span data-stu-id="ef63b-155">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="ef63b-156">Atributos do manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="ef63b-156">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="ef63b-157">Você pode usar atributos do manifesto do assembly para fornecer informações no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-157">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="ef63b-158">Isso inclui título, descrição, alias padrão e configuração.</span><span class="sxs-lookup"><span data-stu-id="ef63b-158">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="ef63b-159">A tabela a seguir mostra os atributos de manifesto do assembly definidos no <xref:System.Reflection?displayProperty=fullName>namespace.</xref:System.Reflection?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ef63b-159">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="ef63b-160">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-160">Attribute</span></span>|<span data-ttu-id="ef63b-161">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ef63b-161">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="ef63b-162"><xref:System.Reflection.AssemblyTitleAttribute></xref:System.Reflection.AssemblyTitleAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-162"><xref:System.Reflection.AssemblyTitleAttribute></span></span>|<span data-ttu-id="ef63b-163">Define um atributo personalizado que especifica um título de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-163">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-164"><xref:System.Reflection.AssemblyDescriptionAttribute></xref:System.Reflection.AssemblyDescriptionAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-164"><xref:System.Reflection.AssemblyDescriptionAttribute></span></span>|<span data-ttu-id="ef63b-165">Define um atributo personalizado que especifica uma descrição de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-165">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-166"><xref:System.Reflection.AssemblyConfigurationAttribute></xref:System.Reflection.AssemblyConfigurationAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-166"><xref:System.Reflection.AssemblyConfigurationAttribute></span></span>|<span data-ttu-id="ef63b-167">Define um atributo personalizado que especifica uma configuração de assembly (como comercial ou de depuração) para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="ef63b-167">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<span data-ttu-id="ef63b-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></xref:System.Reflection.AssemblyDefaultAliasAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-168"><xref:System.Reflection.AssemblyDefaultAliasAttribute></span></span>|<span data-ttu-id="ef63b-169">Define um alias amigável padrão para um manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="ef63b-169">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="ef63b-170"><a name="Obsolete"></a>Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="ef63b-170"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="ef63b-171">O `Obsolete` atributo marca uma entidade programa como um que não é recomendado para uso.</span><span class="sxs-lookup"><span data-stu-id="ef63b-171">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="ef63b-172">Cada uso de uma entidade marcado como obsoleto subsequentemente irá gerar um aviso ou erro, dependendo de como o atributo é configurado.</span><span class="sxs-lookup"><span data-stu-id="ef63b-172">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="ef63b-173">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ef63b-173">For example:</span></span>  
  
```vb  
<System.Obsolete("use class B")>   
Class A  
    Sub Method()  
    End Sub  
End Class  
  
Class B  
    <System.Obsolete("use NewMethod", True)>   
    Sub OldMethod()  
    End Sub  
  
    Sub NewMethod()  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="ef63b-174">Neste exemplo o `Obsolete` atributo é aplicado à classe `A` e ao método `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="ef63b-174">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="ef63b-175">Como o segundo argumento do construtor de atributo aplicadas a `B.OldMethod` é definido como `true`, esse método causará um erro do compilador, enquanto usando a classe `A` irá produzir apenas um aviso.</span><span class="sxs-lookup"><span data-stu-id="ef63b-175">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="ef63b-176">Chamando `B.NewMethod`, no entanto, não produz nenhum aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="ef63b-176">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="ef63b-177">A cadeia de caracteres fornecida como o primeiro argumento para o construtor de atributo será exibida como parte do aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="ef63b-177">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="ef63b-178">Por exemplo, quando você usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:</span><span class="sxs-lookup"><span data-stu-id="ef63b-178">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="ef63b-179">Dois avisos para a classe `A` são geradas: uma para a declaração de referência da classe e outra para o construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="ef63b-179">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="ef63b-180">O `Obsolete` atributo pode ser usado sem argumentos, mas incluindo uma explicação de por que o item está obsoleto e o que usar em vez disso, é recomendável.</span><span class="sxs-lookup"><span data-stu-id="ef63b-180">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="ef63b-181">O `Obsolete` atributo é um atributo de uso único e pode ser aplicado a qualquer entidade que permite que os atributos.</span><span class="sxs-lookup"><span data-stu-id="ef63b-181">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="ef63b-182">`Obsolete`é um alias para <xref:System.ObsoleteAttribute>.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-182">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="ef63b-183"><a name="Conditional"></a>Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="ef63b-183"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="ef63b-184">O `Conditional` atributo torna a execução de um método depende de um identificador de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="ef63b-184">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="ef63b-185">O `Conditional` atributo é um alias para <xref:System.Diagnostics.ConditionalAttribute>e pode ser aplicado a um método ou uma classe de atributo</xref:System.Diagnostics.ConditionalAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-185">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="ef63b-186">Neste exemplo, `Conditional` é aplicado a um método para ativar ou desativar a exibição de informações de diagnóstico específicas do programa:</span><span class="sxs-lookup"><span data-stu-id="ef63b-186">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```vb  
#Const TRACE_ON = True  
Imports System  
Imports System.Diagnostics  
Module TestConditionalAttribute  
    Public Class Trace  
        <Conditional("TRACE_ON")>   
        Public Shared Sub Msg(ByVal msg As String)  
            Console.WriteLine(msg)  
        End Sub  
  
    End Class  
  
    Sub Main()  
        Trace.Msg("Now in Main...")  
        Console.WriteLine("Done.")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ef63b-187">Se o `TRACE_ON` identificador não está definido, nenhuma saída de rastreamento será exibida.</span><span class="sxs-lookup"><span data-stu-id="ef63b-187">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="ef63b-188">O `Conditional` atributo é frequentemente usado com o `DEBUG` identificador para habilitar o rastreamento e recursos de log para compilações de depuração, mas não na versão compilações, como esta:</span><span class="sxs-lookup"><span data-stu-id="ef63b-188">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="ef63b-189">Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada é incluída ou omitida.</span><span class="sxs-lookup"><span data-stu-id="ef63b-189">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="ef63b-190">Se o símbolo é definido, a chamada será incluída; Caso contrário, a chamada é omitida.</span><span class="sxs-lookup"><span data-stu-id="ef63b-190">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="ef63b-191">Usando `Conditional` é um cartucho de limpeza, alternativa mais elegante e menos propensa a colocar métodos dentro de `#if…#endif` blocos, como este:</span><span class="sxs-lookup"><span data-stu-id="ef63b-191">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="ef63b-192">Um método condicional deve ser um método em uma declaração de classe ou estrutura e não deve ter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="ef63b-192">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="ef63b-193">Usando vários identificadores</span><span class="sxs-lookup"><span data-stu-id="ef63b-193">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="ef63b-194">Se um método com várias `Conditional` atributos, uma chamada para o método é incluída se pelo menos um dos símbolos condicionais é definido (em outras palavras, os símbolos são logicamente vinculados usando o operador OR).</span><span class="sxs-lookup"><span data-stu-id="ef63b-194">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="ef63b-195">Neste exemplo, a presença do `A` ou `B` resultará em uma chamada de método:</span><span class="sxs-lookup"><span data-stu-id="ef63b-195">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="ef63b-196">Para obter o efeito da vinculação logicamente símbolos usando o operador AND, você pode definir métodos condicionais seriais.</span><span class="sxs-lookup"><span data-stu-id="ef63b-196">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="ef63b-197">Por exemplo, o segundo método abaixo será executada somente se ambos os `A` e `B` são definidos:</span><span class="sxs-lookup"><span data-stu-id="ef63b-197">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```vb  
<Conditional("A")>   
Shared Sub DoIfA()  
    DoIfAandB()  
End Sub  
  
<Conditional("B")>   
Shared Sub DoIfAandB()  
    ' Code to execute when both A and B are defined...  
End Sub  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="ef63b-198">Usar condicional com Classes de atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-198">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="ef63b-199">O `Conditional` atributo também pode ser aplicado a uma definição de classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-199">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="ef63b-200">Neste exemplo, o atributo personalizado `Documentation` apenas adicionará informações de metadados se DEBUG é definido.</span><span class="sxs-lookup"><span data-stu-id="ef63b-200">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Public Class Documentation  
    Inherits System.Attribute  
    Private text As String  
    Sub New(ByVal doc_text As String)  
        text = doc_text  
    End Sub  
End Class  
  
Class SampleClass  
    ' This attribute will only be included if DEBUG is defined.  
    <Documentation("This method displays an integer.")>   
    Shared Sub DoWork(ByVal i As Integer)  
        System.Console.WriteLine(i)  
    End Sub  
End Class  
```  
  
##  <span data-ttu-id="ef63b-201"><a name="CallerInfo"></a>Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="ef63b-201"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="ef63b-202">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="ef63b-202">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="ef63b-203">Você pode obter o caminho do arquivo do código-fonte, o número da linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="ef63b-203">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="ef63b-204">Para obter informações do chamador do membro, você deve usar os atributos que são aplicados aos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="ef63b-204">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="ef63b-205">Cada parâmetro opcional especifica um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="ef63b-205">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="ef63b-206">A tabela a seguir lista os atributos de informações do chamador que são definidos na <xref:System.Runtime.CompilerServices?displayProperty=fullName>namespace:</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ef63b-206">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="ef63b-207">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-207">Attribute</span></span>|<span data-ttu-id="ef63b-208">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef63b-208">Description</span></span>|<span data-ttu-id="ef63b-209">Tipo</span><span class="sxs-lookup"><span data-stu-id="ef63b-209">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="ef63b-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-210"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="ef63b-211">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="ef63b-211">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="ef63b-212">Este é o caminho em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="ef63b-212">This is the path at compile time.</span></span>|`String`|  
|<span data-ttu-id="ef63b-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-213"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="ef63b-214">Número da linha no arquivo de origem do qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="ef63b-214">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="ef63b-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-215"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="ef63b-216">Nome do método ou o nome da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="ef63b-216">Method name or property name of the caller.</span></span> <span data-ttu-id="ef63b-217">Para obter mais informações, consulte [informações de chamador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="ef63b-217">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="ef63b-218">Para obter mais informações sobre os atributos de informações do chamador, consulte [informações de chamador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="ef63b-218">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <span data-ttu-id="ef63b-219"><a name="VB"></a>Atributos do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ef63b-219"><a name="VB"></a> Visual Basic Attributes</span></span>  
 <span data-ttu-id="ef63b-220">A tabela a seguir lista os atributos que são específicos para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef63b-220">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="ef63b-221">Atributo</span><span class="sxs-lookup"><span data-stu-id="ef63b-221">Attribute</span></span>|<span data-ttu-id="ef63b-222">Finalidade</span><span class="sxs-lookup"><span data-stu-id="ef63b-222">Purpose</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="ef63b-223"><xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-223"><xref:Microsoft.VisualBasic.ComClassAttribute></span></span>|<span data-ttu-id="ef63b-224">Indica para o compilador que a classe deve ser exposta como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="ef63b-224">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<span data-ttu-id="ef63b-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></xref:Microsoft.VisualBasic.HideModuleNameAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-225"><xref:Microsoft.VisualBasic.HideModuleNameAttribute></span></span>|<span data-ttu-id="ef63b-226">Permite que membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-226">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<span data-ttu-id="ef63b-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></xref:Microsoft.VisualBasic.VBFixedStringAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-227"><xref:Microsoft.VisualBasic.VBFixedStringAttribute></span></span>|<span data-ttu-id="ef63b-228">Especifica o tamanho de uma cadeia de caracteres de comprimento fixo em uma estrutura para uso com o arquivo de entrada e saída funções.</span><span class="sxs-lookup"><span data-stu-id="ef63b-228">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<span data-ttu-id="ef63b-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-229"><xref:Microsoft.VisualBasic.VBFixedArrayAttribute></span></span>|<span data-ttu-id="ef63b-230">Especifica o tamanho de uma matriz fixa em uma estrutura para uso com o arquivo de entrada e saída funções.</span><span class="sxs-lookup"><span data-stu-id="ef63b-230">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="ef63b-231">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="ef63b-231">COMClassAttribute</span></span>  
 <span data-ttu-id="ef63b-232">Use `COMClassAttribute` para simplificar o processo de criação componentes COM do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef63b-232">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="ef63b-233">Objetos COM são consideravelmente diferentes de assemblies do .NET Framework e sem `COMClassAttribute`, você precisa seguir uma série de etapas para gerar um objeto COM do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef63b-233">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="ef63b-234">Para classes marcadas com `COMClassAttribute`, o compilador executa muitos desses passos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ef63b-234">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="ef63b-235">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="ef63b-235">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="ef63b-236">Use `HideModuleNameAttribute` para permitir que membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-236">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="ef63b-237">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="ef63b-237">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="ef63b-238">Use `VBFixedStringAttribute` para forçar o Visual Basic para criar uma cadeia de caracteres de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="ef63b-238">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="ef63b-239">Cadeias de caracteres são de comprimento variável por padrão, e esse atributo é útil para armazenar cadeias de caracteres em arquivos.</span><span class="sxs-lookup"><span data-stu-id="ef63b-239">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="ef63b-240">O código a seguir demonstra isso:</span><span class="sxs-lookup"><span data-stu-id="ef63b-240">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="ef63b-241">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="ef63b-241">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="ef63b-242">Use `VBFixedArrayAttribute` para declarar matrizes que foram fixadas em tamanho.</span><span class="sxs-lookup"><span data-stu-id="ef63b-242">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="ef63b-243">Como cadeias de caracteres do Visual Basic, as matrizes são de comprimento variável por padrão.</span><span class="sxs-lookup"><span data-stu-id="ef63b-243">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="ef63b-244">Esse atributo é útil para serialização ou grava dados em arquivos.</span><span class="sxs-lookup"><span data-stu-id="ef63b-244">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef63b-245">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef63b-245">See Also</span></span>  
 <span data-ttu-id="ef63b-246"><xref:System.Reflection></xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="ef63b-246"><xref:System.Reflection></span></span>   
 <span data-ttu-id="ef63b-247"><xref:System.Attribute></xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="ef63b-247"><xref:System.Attribute></span></span>   
<span data-ttu-id="ef63b-248"> [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ef63b-248"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="ef63b-249"> [Atributos](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="ef63b-249"> [Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
<span data-ttu-id="ef63b-250"> [Reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="ef63b-250"> [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md) </span></span>  
<span data-ttu-id="ef63b-251"> [Acessando atributos usando reflexão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="ef63b-251"> [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)</span></span>
