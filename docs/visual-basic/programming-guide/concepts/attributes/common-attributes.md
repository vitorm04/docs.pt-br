---
title: Atributos comuns (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11fe4894-1bf9-4525-a36b-cddcd3a5d22b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4781e7ee60017455796d460d8d7bddb9f7c49676
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="common-attributes-visual-basic"></a><span data-ttu-id="d6d94-102">Atributos comuns (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6d94-102">Common Attributes (Visual Basic)</span></span>
<span data-ttu-id="d6d94-103">Este tópico descreve os atributos que são mais comumente usados em programas em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6d94-103">This topic describes the attributes that are most commonly used in Visual Basic programs.</span></span>  
  
-   [<span data-ttu-id="d6d94-104">Atributos globais</span><span class="sxs-lookup"><span data-stu-id="d6d94-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="d6d94-105">Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="d6d94-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="d6d94-106">Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="d6d94-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="d6d94-107">Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="d6d94-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
-   [<span data-ttu-id="d6d94-108">Atributos do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6d94-108">Visual Basic Attributes</span></span>](#VB)  
  
##  <a name="Global"></a> <span data-ttu-id="d6d94-109">Atributos globais</span><span class="sxs-lookup"><span data-stu-id="d6d94-109">Global Attributes</span></span>  
 <span data-ttu-id="d6d94-110">A maioria dos atributos são aplicados aos elementos específicos de linguagem, como classes ou métodos. No entanto, alguns atributos são globais. Eles se aplicam a um assembly inteiro ou módulo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-110">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="d6d94-111">Por exemplo, o atributo <xref:System.Reflection.AssemblyVersionAttribute> pode ser usado para inserir informações de versão em um assembly, desta maneira:</span><span class="sxs-lookup"><span data-stu-id="d6d94-111">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```vb  
<Assembly: AssemblyVersion("1.0.0.0")>  
```  
  
 <span data-ttu-id="d6d94-112">Atributos globais aparecem no código-fonte após qualquer nível superior `Imports` instruções e antes de quaisquer declarações de namespace, módulo ou tipo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-112">Global attributes appear in the source code after any top-level `Imports` statements and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="d6d94-113">Os atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser compilados em uma única passagem de compilação.</span><span class="sxs-lookup"><span data-stu-id="d6d94-113">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="d6d94-114">Para projetos do Visual Basic, os atributos globais geralmente são colocados no arquivo AssemblyInfo (o arquivo é criado automaticamente quando você cria um projeto no Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="d6d94-114">For Visual Basic projects, global attributes are generally put in the AssemblyInfo.vb file (the file is created automatically when you create a project in Visual Studio).</span></span>  
  
 <span data-ttu-id="d6d94-115">Os atributos de assembly são valores que fornecem informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-115">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="d6d94-116">Eles se enquadram nas seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="d6d94-116">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="d6d94-117">Atributos de identidade do assembly</span><span class="sxs-lookup"><span data-stu-id="d6d94-117">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="d6d94-118">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="d6d94-118">Informational attributes</span></span>  
  
-   <span data-ttu-id="d6d94-119">Atributos de manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="d6d94-119">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="d6d94-120">Atributos de Identidade do Assembly</span><span class="sxs-lookup"><span data-stu-id="d6d94-120">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="d6d94-121">Três atributos (com um nome forte, se aplicável) determinam a identidade de um assembly: nome, versão e cultura.</span><span class="sxs-lookup"><span data-stu-id="d6d94-121">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="d6d94-122">Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código.</span><span class="sxs-lookup"><span data-stu-id="d6d94-122">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="d6d94-123">Você pode definir a versão e a cultura de um assembly, usando atributos.</span><span class="sxs-lookup"><span data-stu-id="d6d94-123">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="d6d94-124">No entanto, o valor do nome é definido pelo compilador, pelo IDE do Visual Studio na [caixa de diálogo de Informações do Assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou pelo Assembly Linker (Al.exe) quando o assembly é criado, com base no arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-124">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="d6d94-125">O atributo <xref:System.Reflection.AssemblyFlagsAttribute> especifica se várias cópias do assembly podem coexistir.</span><span class="sxs-lookup"><span data-stu-id="d6d94-125">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="d6d94-126">A tabela a seguir mostra os atributos de identidade.</span><span class="sxs-lookup"><span data-stu-id="d6d94-126">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="d6d94-127">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6d94-127">Attribute</span></span>|<span data-ttu-id="d6d94-128">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d6d94-128">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="d6d94-129">Descreve completamente a identidade de um assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-129">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="d6d94-130">Especifica a versão de um assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-130">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="d6d94-131">Especifica a qual cultura o assembly dá suporte.</span><span class="sxs-lookup"><span data-stu-id="d6d94-131">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="d6d94-132">Especifica se um assembly dá suporte à execução lado a lado no mesmo computador, no mesmo processo ou no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-132">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="d6d94-133">Atributos Informativos</span><span class="sxs-lookup"><span data-stu-id="d6d94-133">Informational Attributes</span></span>  
 <span data-ttu-id="d6d94-134">Você pode usar atributos informativos para fornecer informações adicionais corporativas ou de produto para um assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-134">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="d6d94-135">A tabela a seguir mostra os atributos informativos definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6d94-135">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="d6d94-136">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6d94-136">Attribute</span></span>|<span data-ttu-id="d6d94-137">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d6d94-137">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="d6d94-138">Define um atributo personalizado que especifica um nome de produto para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-138">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="d6d94-139">Define um atributo personalizado que especifica uma marca registrada para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-139">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="d6d94-140">Define um atributo personalizado que especifica uma versão informativa para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-140">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="d6d94-141">Define um atributo personalizado que especifica um nome de empresa para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-141">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="d6d94-142">Define um atributo personalizado que especifica os direitos autorais para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-142">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="d6d94-143">Instrui o compilador a usar um número de versão específico para o recurso de versão de arquivo do Win32.</span><span class="sxs-lookup"><span data-stu-id="d6d94-143">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="d6d94-144">Indica se o assembly está em conformidade com a CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="d6d94-144">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="d6d94-145">Atributos de Manifesto do Assembly</span><span class="sxs-lookup"><span data-stu-id="d6d94-145">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="d6d94-146">Você pode usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-146">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="d6d94-147">Isso inclui título, descrição, alias padrão e configuração.</span><span class="sxs-lookup"><span data-stu-id="d6d94-147">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="d6d94-148">A tabela a seguir mostra os atributos de manifesto do assembly definidos no namespace <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d6d94-148">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=nameWithType> namespace.</span></span>  
  
|<span data-ttu-id="d6d94-149">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6d94-149">Attribute</span></span>|<span data-ttu-id="d6d94-150">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d6d94-150">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="d6d94-151">Define um atributo personalizado que especifica um título de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-151">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="d6d94-152">Define um atributo personalizado que especifica uma descrição de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-152">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="d6d94-153">Define um atributo personalizado que especifica uma configuração de assembly (como comercial ou de depuração) para um manifesto do assembly. assembly.</span><span class="sxs-lookup"><span data-stu-id="d6d94-153">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="d6d94-154">Define um alias amigável padrão para um manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="d6d94-154">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <a name="Obsolete"></a> <span data-ttu-id="d6d94-155">Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="d6d94-155">Obsolete Attribute</span></span>  
 <span data-ttu-id="d6d94-156">O atributo `Obsolete` marca uma entidade programa como não recomendada para uso.</span><span class="sxs-lookup"><span data-stu-id="d6d94-156">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="d6d94-157">Cada uso de uma entidade marcada como obsoleta gerará subsequentemente um aviso ou erro, dependendo de como o atributo é configurado.</span><span class="sxs-lookup"><span data-stu-id="d6d94-157">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="d6d94-158">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d6d94-158">For example:</span></span>  
  
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
  
 <span data-ttu-id="d6d94-159">Neste exemplo o atributo `Obsolete` é aplicado à classe `A` e ao método `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="d6d94-159">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="d6d94-160">Como o segundo argumento do construtor de atributo aplicado a `B.OldMethod` está definido como `true`, esse método causará um erro do compilador, enquanto que ao usar a classe `A`, produzirá apenas um aviso.</span><span class="sxs-lookup"><span data-stu-id="d6d94-160">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="d6d94-161">Chamar `B.NewMethod`, no entanto, não produz aviso nem erro.</span><span class="sxs-lookup"><span data-stu-id="d6d94-161">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="d6d94-162">A cadeia de caracteres fornecida como o primeiro argumento para o construtor de atributo será exibida como parte do aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="d6d94-162">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="d6d94-163">Por exemplo, ao usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:</span><span class="sxs-lookup"><span data-stu-id="d6d94-163">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```vb  
' Generates 2 warnings:  
' Dim a As New A  
' Generate no errors or warnings:  
  
Dim b As New B  
b.NewMethod()  
  
' Generates an error, terminating compilation:  
' b.OldMethod()  
```  
  
 <span data-ttu-id="d6d94-164">São gerados dois avisos para a classe `A`: um para a declaração da referência de classe e outro para o construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="d6d94-164">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="d6d94-165">O atributo `Obsolete` pode ser usado sem argumentos, mas é recomendável incluir uma explicação de por que o item está obsoleto e o que deve ser usado no lugar dele.</span><span class="sxs-lookup"><span data-stu-id="d6d94-165">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="d6d94-166">O atributo `Obsolete` é um atributo de uso único e pode ser aplicado a qualquer entidade que permite atributos.</span><span class="sxs-lookup"><span data-stu-id="d6d94-166">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="d6d94-167">`Obsolete` é um alias para <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d6d94-167">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <a name="Conditional"></a> <span data-ttu-id="d6d94-168">Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="d6d94-168">Conditional Attribute</span></span>  
 <span data-ttu-id="d6d94-169">O atributo `Conditional` torna a execução de um método dependente de um identificador de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="d6d94-169">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="d6d94-170">O atributo `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute> e pode ser aplicado a um método ou uma classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-170">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="d6d94-171">Neste exemplo, `Conditional` é aplicado a um método para habilitar ou desabilitar a exibição de informações de diagnóstico específicas do programa:</span><span class="sxs-lookup"><span data-stu-id="d6d94-171">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
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
  
 <span data-ttu-id="d6d94-172">Se o identificador `TRACE_ON` não estiver definido, nenhuma saída de rastreamento será exibida.</span><span class="sxs-lookup"><span data-stu-id="d6d94-172">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="d6d94-173">O atributo `Conditional` é frequentemente usado com o identificador `DEBUG` para habilitar recursos de rastreamento e de registro em log para builds de depuração, mas não em builds de versão, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="d6d94-173">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```vb  
<Conditional("DEBUG")>   
Shared Sub DebugMethod()  
  
End Sub  
```  
  
 <span data-ttu-id="d6d94-174">Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada será incluída ou omitida.</span><span class="sxs-lookup"><span data-stu-id="d6d94-174">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="d6d94-175">Se o símbolo estiver definido, a chamada será incluída, caso contrário, a chamada será omitida.</span><span class="sxs-lookup"><span data-stu-id="d6d94-175">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="d6d94-176">O uso de `Conditional` é uma alternativa mais limpa, mais elegante e menos propensa a erros para incluir métodos dentro de blocos `#if…#endif`, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="d6d94-176">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```vb  
#If DEBUG Then  
    Sub ConditionalMethod()  
    End Sub  
#End If  
```  
  
 <span data-ttu-id="d6d94-177">Um método condicional deve ser um método em uma declaração de classe ou de struct e não deve ter um valor retornado.</span><span class="sxs-lookup"><span data-stu-id="d6d94-177">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="d6d94-178">Usando vários identificadores</span><span class="sxs-lookup"><span data-stu-id="d6d94-178">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="d6d94-179">Se um método tem vários atributos `Conditional`, uma chamada para o método será incluída se pelo menos um dos símbolos condicionais for definido (em outras palavras, os símbolos são logicamente vinculados através do uso do operador OR).</span><span class="sxs-lookup"><span data-stu-id="d6d94-179">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="d6d94-180">Neste exemplo, a presença de `A` ou `B` resultará em uma chamada de método:</span><span class="sxs-lookup"><span data-stu-id="d6d94-180">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```vb  
<Conditional("A"), Conditional("B")>   
Shared Sub DoIfAorB()  
  
End Sub  
```  
  
 <span data-ttu-id="d6d94-181">Para alcançar o efeito da vinculação lógica de símbolos usando o operador AND, você pode definir métodos condicionais em série.</span><span class="sxs-lookup"><span data-stu-id="d6d94-181">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="d6d94-182">Por exemplo, o segundo método abaixo será executado somente se `A` e `B` estiverem definidos:</span><span class="sxs-lookup"><span data-stu-id="d6d94-182">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
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
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="d6d94-183">Usando condicional com classes de atributos</span><span class="sxs-lookup"><span data-stu-id="d6d94-183">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="d6d94-184">O atributo `Conditional` também pode ser aplicado a uma definição de classe de atributos.</span><span class="sxs-lookup"><span data-stu-id="d6d94-184">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="d6d94-185">Neste exemplo, o atributo personalizado `Documentation` só adicionará informações aos metadados se DEBUG estiver definido.</span><span class="sxs-lookup"><span data-stu-id="d6d94-185">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
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
  
##  <a name="CallerInfo"></a> <span data-ttu-id="d6d94-186">Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="d6d94-186">Caller Info Attributes</span></span>  
 <span data-ttu-id="d6d94-187">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="d6d94-187">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="d6d94-188">Você pode obter o caminho do arquivo do código-fonte, o número de linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="d6d94-188">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="d6d94-189">Para obter informações do chamador do membro, você usa os atributos que são aplicados aos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="d6d94-189">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="d6d94-190">Cada parâmetro opcional especifica um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="d6d94-190">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="d6d94-191">A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="d6d94-191">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="d6d94-192">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6d94-192">Attribute</span></span>|<span data-ttu-id="d6d94-193">Descrição</span><span class="sxs-lookup"><span data-stu-id="d6d94-193">Description</span></span>|<span data-ttu-id="d6d94-194">Tipo</span><span class="sxs-lookup"><span data-stu-id="d6d94-194">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="d6d94-195">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="d6d94-195">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="d6d94-196">Esse é o caminho em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="d6d94-196">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="d6d94-197">Número de linha no arquivo de origem do qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="d6d94-197">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="d6d94-198">Nome do método ou nome da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="d6d94-198">Method name or property name of the caller.</span></span> <span data-ttu-id="d6d94-199">Para obter mais informações, consulte [informações de chamador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="d6d94-199">For more information, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="d6d94-200">Para obter mais informações sobre os atributos de informações do chamador, consulte [informações de chamador (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="d6d94-200">For more information about the Caller Info attributes, see [Caller Information (Visual Basic)](../../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
##  <a name="VB"></a><span data-ttu-id="d6d94-201">Atributos do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6d94-201">Visual Basic Attributes</span></span>  
 <span data-ttu-id="d6d94-202">A tabela a seguir lista os atributos que são específicos para o Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6d94-202">The following table lists the attributes that are specific to Visual Basic.</span></span>  
  
|<span data-ttu-id="d6d94-203">Atributo</span><span class="sxs-lookup"><span data-stu-id="d6d94-203">Attribute</span></span>|<span data-ttu-id="d6d94-204">Finalidade</span><span class="sxs-lookup"><span data-stu-id="d6d94-204">Purpose</span></span>|  
|---------------|-------------|  
|<xref:Microsoft.VisualBasic.ComClassAttribute>|<span data-ttu-id="d6d94-205">Indica para o compilador que a classe deve ser exposta como um objeto COM.</span><span class="sxs-lookup"><span data-stu-id="d6d94-205">Indicates to the compiler that the class should be exposed as a COM object.</span></span>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute>|<span data-ttu-id="d6d94-206">Permite que membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-206">Allows module members to be accessed using only the qualification needed for the module.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedStringAttribute>|<span data-ttu-id="d6d94-207">Especifica o tamanho de uma cadeia de caracteres de comprimento fixo em uma estrutura para uso com o arquivo de entrada e saída funções.</span><span class="sxs-lookup"><span data-stu-id="d6d94-207">Specifies the size of a fixed-length string in a structure for use with file input and output functions.</span></span>|  
|<xref:Microsoft.VisualBasic.VBFixedArrayAttribute>|<span data-ttu-id="d6d94-208">Especifica o tamanho de uma matriz fixa em uma estrutura para uso com o arquivo de entrada e saída funções.</span><span class="sxs-lookup"><span data-stu-id="d6d94-208">Specifies the size of a fixed array in a structure for use with file input and output functions.</span></span>|  
  
### <a name="comclassattribute"></a><span data-ttu-id="d6d94-209">COMClassAttribute</span><span class="sxs-lookup"><span data-stu-id="d6d94-209">COMClassAttribute</span></span>  
 <span data-ttu-id="d6d94-210">Use `COMClassAttribute` para simplificar o processo de criação componentes COM do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6d94-210">Use `COMClassAttribute` to simplify the process of creating COM components from Visual Basic.</span></span> <span data-ttu-id="d6d94-211">Objetos COM são consideravelmente diferentes dos assemblies do .NET Framework e sem `COMClassAttribute`, você precisa seguir uma série de etapas para gerar um objeto COM do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d6d94-211">COM objects are considerably different from .NET Framework assemblies, and without `COMClassAttribute`, you need to follow a number of steps to generate a COM object from Visual Basic.</span></span> <span data-ttu-id="d6d94-212">Para classes marcadas com `COMClassAttribute`, o compilador executa muitos desses passos automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d6d94-212">For classes marked with `COMClassAttribute`, the compiler performs many of these steps automatically.</span></span>  
  
### <a name="hidemodulenameattribute"></a><span data-ttu-id="d6d94-213">HideModuleNameAttribute</span><span class="sxs-lookup"><span data-stu-id="d6d94-213">HideModuleNameAttribute</span></span>  
 <span data-ttu-id="d6d94-214">Use `HideModuleNameAttribute` para permitir que os membros de módulo sejam acessados usando somente a qualificação necessária para o módulo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-214">Use `HideModuleNameAttribute` to allow module members to be accessed by using only the qualification needed for the module.</span></span>  
  
### <a name="vbfixedstringattribute"></a><span data-ttu-id="d6d94-215">VBFixedStringAttribute</span><span class="sxs-lookup"><span data-stu-id="d6d94-215">VBFixedStringAttribute</span></span>  
 <span data-ttu-id="d6d94-216">Use `VBFixedStringAttribute` para forçar o Visual Basic para criar uma cadeia de caracteres de comprimento fixo.</span><span class="sxs-lookup"><span data-stu-id="d6d94-216">Use `VBFixedStringAttribute` to force Visual Basic to create a fixed-length string.</span></span> <span data-ttu-id="d6d94-217">Cadeias de caracteres são de comprimento variável por padrão, e esse atributo é útil para armazenar cadeias de caracteres em arquivos.</span><span class="sxs-lookup"><span data-stu-id="d6d94-217">Strings are of variable length by default, and this attribute is useful when storing strings to files.</span></span> <span data-ttu-id="d6d94-218">O código a seguir demonstra isso:</span><span class="sxs-lookup"><span data-stu-id="d6d94-218">The following code demonstrates this:</span></span>  
  
```vb  
Structure Worker  
    ' The runtime uses VBFixedString to determine   
    ' if the field should be written out as a fixed size.  
    <VBFixedString(10)> Public LastName As String  
    <VBFixedString(7)> Public Title As String  
    <VBFixedString(2)> Public Rank As String  
End Structure  
```  
  
### <a name="vbfixedarrayattribute"></a><span data-ttu-id="d6d94-219">VBFixedArrayAttribute</span><span class="sxs-lookup"><span data-stu-id="d6d94-219">VBFixedArrayAttribute</span></span>  
 <span data-ttu-id="d6d94-220">Use `VBFixedArrayAttribute` para declarar matrizes que foram corrigidas no tamanho.</span><span class="sxs-lookup"><span data-stu-id="d6d94-220">Use `VBFixedArrayAttribute` to declare arrays that are fixed in size.</span></span> <span data-ttu-id="d6d94-221">Como cadeias de caracteres do Visual Basic, as matrizes são de comprimento variável por padrão.</span><span class="sxs-lookup"><span data-stu-id="d6d94-221">Like Visual Basic strings, arrays are of variable length by default.</span></span> <span data-ttu-id="d6d94-222">Esse atributo é útil ao serializar ou grava dados em arquivos.</span><span class="sxs-lookup"><span data-stu-id="d6d94-222">This attribute is useful when serializing or writing data to files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6d94-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6d94-223">See Also</span></span>  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [<span data-ttu-id="d6d94-224">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6d94-224">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)  
 [<span data-ttu-id="d6d94-225">Atributos</span><span class="sxs-lookup"><span data-stu-id="d6d94-225">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)  
 [<span data-ttu-id="d6d94-226">Reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6d94-226">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="d6d94-227">Acessando atributos usando reflexão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6d94-227">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
