---
title: Atributos comuns (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 785a0526-6c0e-4599-8c61-ccdc88dd9965
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: b03d44a7cf48adee593f749eb4d0d6dbec061b9d
ms.openlocfilehash: 51e0b382ac3257540de3226c370a4704aca74933
ms.contentlocale: pt-br
ms.lasthandoff: 08/29/2017

---
# <a name="common-attributes-c"></a><span data-ttu-id="b0af6-102">Atributos comuns (C#)</span><span class="sxs-lookup"><span data-stu-id="b0af6-102">Common Attributes (C#)</span></span>
<span data-ttu-id="b0af6-103">Este tópico descreve os atributos que são mais comumente usados nos programas em C#.</span><span class="sxs-lookup"><span data-stu-id="b0af6-103">This topic describes the attributes that are most commonly used in C# programs.</span></span>  
  
-   [<span data-ttu-id="b0af6-104">Atributos globais</span><span class="sxs-lookup"><span data-stu-id="b0af6-104">Global Attributes</span></span>](#Global)  
  
-   [<span data-ttu-id="b0af6-105">Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="b0af6-105">Obsolete Attribute</span></span>](#Obsolete)  
  
-   [<span data-ttu-id="b0af6-106">Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="b0af6-106">Conditional Attribute</span></span>](#Conditional)  
  
-   [<span data-ttu-id="b0af6-107">Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="b0af6-107">Caller Info Attributes</span></span>](#CallerInfo)  
  
##  <span data-ttu-id="b0af6-108"><a name="Global"></a> Atributos globais</span><span class="sxs-lookup"><span data-stu-id="b0af6-108"><a name="Global"></a> Global Attributes</span></span>  
 <span data-ttu-id="b0af6-109">A maioria dos atributos são aplicados aos elementos específicos de linguagem, como classes ou métodos. No entanto, alguns atributos são globais. Eles se aplicam a um assembly inteiro ou módulo.</span><span class="sxs-lookup"><span data-stu-id="b0af6-109">Most attributes are applied to specific language elements such as classes or methods; however, some attributes are global—they apply to an entire assembly or module.</span></span> <span data-ttu-id="b0af6-110">Por exemplo, o atributo <xref:System.Reflection.AssemblyVersionAttribute> pode ser usado para inserir informações de versão em um assembly, desta maneira:</span><span class="sxs-lookup"><span data-stu-id="b0af6-110">For example, the <xref:System.Reflection.AssemblyVersionAttribute> attribute can be used to embed version information into an assembly, like this:</span></span>  
  
```csharp  
[assembly: AssemblyVersion("1.0.0.0")]  
```  
  
 <span data-ttu-id="b0af6-111">Os atributos globais aparecem no código-fonte depois de qualquer diretiva `using` de nível superior e antes de qualquer declaração de namespace, módulo ou tipo.</span><span class="sxs-lookup"><span data-stu-id="b0af6-111">Global attributes appear in the source code after any top-level `using` directives and before any type, module, or namespace declarations.</span></span> <span data-ttu-id="b0af6-112">Os atributos globais podem aparecer em vários arquivos de origem, mas os arquivos devem ser compilados em uma única passagem de compilação.</span><span class="sxs-lookup"><span data-stu-id="b0af6-112">Global attributes can appear in multiple source files, but the files must be compiled in a single compilation pass.</span></span> <span data-ttu-id="b0af6-113">Em projetos do C#, os atributos globais são colocados no arquivo AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="b0af6-113">In C# projects, global attributes are put in the AssemblyInfo.cs file.</span></span>  
  
 <span data-ttu-id="b0af6-114">Os atributos de assembly são valores que fornecem informações sobre um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-114">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="b0af6-115">Eles se enquadram nas seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="b0af6-115">They fall into the following categories:</span></span>  
  
-   <span data-ttu-id="b0af6-116">Atributos de identidade do assembly</span><span class="sxs-lookup"><span data-stu-id="b0af6-116">Assembly identity attributes</span></span>  
  
-   <span data-ttu-id="b0af6-117">Atributos informativos</span><span class="sxs-lookup"><span data-stu-id="b0af6-117">Informational attributes</span></span>  
  
-   <span data-ttu-id="b0af6-118">Atributos de manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="b0af6-118">Assembly manifest attributes</span></span>  
  
### <a name="assembly-identity-attributes"></a><span data-ttu-id="b0af6-119">Atributos de Identidade do Assembly</span><span class="sxs-lookup"><span data-stu-id="b0af6-119">Assembly Identity Attributes</span></span>  
 <span data-ttu-id="b0af6-120">Três atributos (com um nome forte, se aplicável) determinam a identidade de um assembly: nome, versão e cultura.</span><span class="sxs-lookup"><span data-stu-id="b0af6-120">Three attributes (with a strong name, if applicable) determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="b0af6-121">Esses atributos formam o nome completo do assembly e são necessários ao fazer referência a ele no código.</span><span class="sxs-lookup"><span data-stu-id="b0af6-121">These attributes form the full name of the assembly and are required when you reference it in code.</span></span> <span data-ttu-id="b0af6-122">Você pode definir a versão e a cultura de um assembly, usando atributos.</span><span class="sxs-lookup"><span data-stu-id="b0af6-122">You can set an assembly's version and culture using attributes.</span></span> <span data-ttu-id="b0af6-123">No entanto, o valor do nome é definido pelo compilador, pelo IDE do Visual Studio na [caixa de diálogo de Informações do Assembly](/visualstudio/ide/reference/assembly-information-dialog-box) ou pelo Assembly Linker (Al.exe) quando o assembly é criado, com base no arquivo que contém o manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-123">However, the name value is set by the compiler, the Visual Studio IDE in the [Assembly Information Dialog Box](/visualstudio/ide/reference/assembly-information-dialog-box), or the Assembly Linker (Al.exe) when the assembly is created, based on the file that contains the assembly manifest.</span></span> <span data-ttu-id="b0af6-124">O atributo <xref:System.Reflection.AssemblyFlagsAttribute> especifica se várias cópias do assembly podem coexistir.</span><span class="sxs-lookup"><span data-stu-id="b0af6-124">The <xref:System.Reflection.AssemblyFlagsAttribute> attribute specifies whether multiple copies of the assembly can coexist.</span></span>  
  
 <span data-ttu-id="b0af6-125">A tabela a seguir mostra os atributos de identidade.</span><span class="sxs-lookup"><span data-stu-id="b0af6-125">The following table shows the identity attributes.</span></span>  
  
|<span data-ttu-id="b0af6-126">Atributo</span><span class="sxs-lookup"><span data-stu-id="b0af6-126">Attribute</span></span>|<span data-ttu-id="b0af6-127">Finalidade</span><span class="sxs-lookup"><span data-stu-id="b0af6-127">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyName>|<span data-ttu-id="b0af6-128">Descreve completamente a identidade de um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-128">Fully describes the identity of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="b0af6-129">Especifica a versão de um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-129">Specifies the version of an assembly.</span></span>|  
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="b0af6-130">Especifica a qual cultura o assembly dá suporte.</span><span class="sxs-lookup"><span data-stu-id="b0af6-130">Specifies which culture the assembly supports.</span></span>|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="b0af6-131">Especifica se um assembly dá suporte à execução lado a lado no mesmo computador, no mesmo processo ou no mesmo domínio do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b0af6-131">Specifies whether an assembly supports side-by-side execution on the same computer, in the same process, or in the same application domain.</span></span>|  
  
### <a name="informational-attributes"></a><span data-ttu-id="b0af6-132">Atributos Informativos</span><span class="sxs-lookup"><span data-stu-id="b0af6-132">Informational Attributes</span></span>  
 <span data-ttu-id="b0af6-133">Você pode usar atributos informativos para fornecer informações adicionais corporativas ou de produto para um assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-133">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="b0af6-134">A tabela a seguir mostra os atributos informativos definidos no namespace <xref:System.Reflection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b0af6-134">The following table shows the informational attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="b0af6-135">Atributo</span><span class="sxs-lookup"><span data-stu-id="b0af6-135">Attribute</span></span>|<span data-ttu-id="b0af6-136">Finalidade</span><span class="sxs-lookup"><span data-stu-id="b0af6-136">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="b0af6-137">Define um atributo personalizado que especifica um nome de produto para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-137">Defines a custom attribute that specifies a product name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="b0af6-138">Define um atributo personalizado que especifica uma marca registrada para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-138">Defines a custom attribute that specifies a trademark for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="b0af6-139">Define um atributo personalizado que especifica uma versão informativa para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-139">Defines a custom attribute that specifies an informational version for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="b0af6-140">Define um atributo personalizado que especifica um nome de empresa para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-140">Defines a custom attribute that specifies a company name for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="b0af6-141">Define um atributo personalizado que especifica os direitos autorais para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-141">Defines a custom attribute that specifies a copyright for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="b0af6-142">Instrui o compilador a usar um número de versão específico para o recurso de versão de arquivo do Win32.</span><span class="sxs-lookup"><span data-stu-id="b0af6-142">Instructs the compiler to use a specific version number for the Win32 file version resource.</span></span>|  
|<xref:System.CLSCompliantAttribute>|<span data-ttu-id="b0af6-143">Indica se o assembly está em conformidade com a CLS (Common Language Specification).</span><span class="sxs-lookup"><span data-stu-id="b0af6-143">Indicates whether the assembly is compliant with the Common Language Specification (CLS).</span></span>|  
  
### <a name="assembly-manifest-attributes"></a><span data-ttu-id="b0af6-144">Atributos de Manifesto do Assembly</span><span class="sxs-lookup"><span data-stu-id="b0af6-144">Assembly Manifest Attributes</span></span>  
 <span data-ttu-id="b0af6-145">Você pode usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-145">You can use assembly manifest attributes to provide information in the assembly manifest.</span></span> <span data-ttu-id="b0af6-146">Isso inclui título, descrição, alias padrão e configuração.</span><span class="sxs-lookup"><span data-stu-id="b0af6-146">This includes title, description, default alias, and configuration.</span></span> <span data-ttu-id="b0af6-147">A tabela a seguir mostra os atributos de manifesto do assembly definidos no namespace <xref:System.Reflection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="b0af6-147">The following table shows the assembly manifest attributes defined in the <xref:System.Reflection?displayProperty=fullName> namespace.</span></span>  
  
|<span data-ttu-id="b0af6-148">Atributo</span><span class="sxs-lookup"><span data-stu-id="b0af6-148">Attribute</span></span>|<span data-ttu-id="b0af6-149">Finalidade</span><span class="sxs-lookup"><span data-stu-id="b0af6-149">Purpose</span></span>|  
|---------------|-------------|  
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="b0af6-150">Define um atributo personalizado que especifica um título de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-150">Defines a custom attribute that specifies an assembly title for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="b0af6-151">Define um atributo personalizado que especifica uma descrição de assembly para um manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-151">Defines a custom attribute that specifies an assembly description for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="b0af6-152">Define um atributo personalizado que especifica uma configuração de assembly (como comercial ou de depuração) para um manifesto do assembly. assembly.</span><span class="sxs-lookup"><span data-stu-id="b0af6-152">Defines a custom attribute that specifies an assembly configuration (such as retail or debug) for an assembly manifest.</span></span>|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="b0af6-153">Define um alias amigável padrão para um manifesto do assembly</span><span class="sxs-lookup"><span data-stu-id="b0af6-153">Defines a friendly default alias for an assembly manifest</span></span>|  
  
##  <span data-ttu-id="b0af6-154"><a name="Obsolete"></a> Atributo obsoleto</span><span class="sxs-lookup"><span data-stu-id="b0af6-154"><a name="Obsolete"></a> Obsolete Attribute</span></span>  
 <span data-ttu-id="b0af6-155">O atributo `Obsolete` marca uma entidade programa como não recomendada para uso.</span><span class="sxs-lookup"><span data-stu-id="b0af6-155">The `Obsolete` attribute marks a program entity as one that is no longer recommended for use.</span></span> <span data-ttu-id="b0af6-156">Cada uso de uma entidade marcada como obsoleta gerará subsequentemente um aviso ou erro, dependendo de como o atributo é configurado.</span><span class="sxs-lookup"><span data-stu-id="b0af6-156">Each use of an entity marked obsolete will subsequently generate a warning or an error, depending on how the attribute is configured.</span></span> <span data-ttu-id="b0af6-157">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b0af6-157">For example:</span></span>  
  
```csharp  
[System.Obsolete("use class B")]  
class A  
{  
    public void Method() { }  
}  
class B  
{  
    [System.Obsolete("use NewMethod", true)]  
    public void OldMethod() { }  
    public void NewMethod() { }  
}  
```  
  
 <span data-ttu-id="b0af6-158">Neste exemplo o atributo `Obsolete` é aplicado à classe `A` e ao método `B.OldMethod`.</span><span class="sxs-lookup"><span data-stu-id="b0af6-158">In this example the `Obsolete` attribute is applied to class `A` and to method `B.OldMethod`.</span></span> <span data-ttu-id="b0af6-159">Como o segundo argumento do construtor de atributo aplicado a `B.OldMethod` está definido como `true`, esse método causará um erro do compilador, enquanto que ao usar a classe `A`, produzirá apenas um aviso.</span><span class="sxs-lookup"><span data-stu-id="b0af6-159">Because the second argument of the attribute constructor applied to `B.OldMethod` is set to `true`, this method will cause a compiler error, whereas using class `A` will just produce a warning.</span></span> <span data-ttu-id="b0af6-160">Chamar `B.NewMethod`, no entanto, não produz aviso nem erro.</span><span class="sxs-lookup"><span data-stu-id="b0af6-160">Calling `B.NewMethod`, however, produces no warning or error.</span></span>  
  
 <span data-ttu-id="b0af6-161">A cadeia de caracteres fornecida como o primeiro argumento para o construtor de atributo será exibida como parte do aviso ou erro.</span><span class="sxs-lookup"><span data-stu-id="b0af6-161">The string provided as the first argument to attribute constructor will be displayed as part of the warning or error.</span></span> <span data-ttu-id="b0af6-162">Por exemplo, ao usá-lo com as definições anteriores, o código a seguir gera um erro e dois avisos:</span><span class="sxs-lookup"><span data-stu-id="b0af6-162">For example, when you use it with the previous definitions, the following code generates two warnings and one error:</span></span>  
  
```csharp  
// Generates 2 warnings:  
// A a = new A();  
  
// Generate no errors or warnings:  
B b = new B();  
b.NewMethod();  
  
// Generates an error, terminating compilation:  
// b.OldMethod();  
```  
  
 <span data-ttu-id="b0af6-163">São gerados dois avisos para a classe `A`: um para a declaração da referência de classe e outro para o construtor de classe.</span><span class="sxs-lookup"><span data-stu-id="b0af6-163">Two warnings for class `A` are generated: one for the declaration of the class reference, and one for the class constructor.</span></span>  
  
 <span data-ttu-id="b0af6-164">O atributo `Obsolete` pode ser usado sem argumentos, mas é recomendável incluir uma explicação de por que o item está obsoleto e o que deve ser usado no lugar dele.</span><span class="sxs-lookup"><span data-stu-id="b0af6-164">The `Obsolete` attribute can be used without arguments, but including an explanation of why the item is obsolete and what to use instead is recommended.</span></span>  
  
 <span data-ttu-id="b0af6-165">O atributo `Obsolete` é um atributo de uso único e pode ser aplicado a qualquer entidade que permite atributos.</span><span class="sxs-lookup"><span data-stu-id="b0af6-165">The `Obsolete` attribute is a single-use attribute and can be applied to any entity that allows attributes.</span></span> <span data-ttu-id="b0af6-166">`Obsolete` é um alias para <xref:System.ObsoleteAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b0af6-166">`Obsolete` is an alias for <xref:System.ObsoleteAttribute>.</span></span>  
  
##  <span data-ttu-id="b0af6-167"><a name="Conditional"></a> Atributo condicional</span><span class="sxs-lookup"><span data-stu-id="b0af6-167"><a name="Conditional"></a> Conditional Attribute</span></span>  
 <span data-ttu-id="b0af6-168">O atributo `Conditional` torna a execução de um método dependente de um identificador de pré-processamento.</span><span class="sxs-lookup"><span data-stu-id="b0af6-168">The `Conditional` attribute makes the execution of a method dependent on a preprocessing identifier.</span></span> <span data-ttu-id="b0af6-169">O atributo `Conditional` é um alias para <xref:System.Diagnostics.ConditionalAttribute> e pode ser aplicado a um método ou uma classe de atributo.</span><span class="sxs-lookup"><span data-stu-id="b0af6-169">The `Conditional` attribute is an alias for <xref:System.Diagnostics.ConditionalAttribute>, and can be applied to a method or an attribute class.</span></span>  
  
 <span data-ttu-id="b0af6-170">Neste exemplo, `Conditional` é aplicado a um método para habilitar ou desabilitar a exibição de informações de diagnóstico específicas do programa:</span><span class="sxs-lookup"><span data-stu-id="b0af6-170">In this example, `Conditional` is applied to a method to enable or disable the display of program-specific diagnostic information:</span></span>  
  
```csharp  
#define TRACE_ON  
using System;  
using System.Diagnostics;  
  
public class Trace  
{  
    [Conditional("TRACE_ON")]  
    public static void Msg(string msg)  
    {  
        Console.WriteLine(msg);  
    }  
}  
  
public class ProgramClass  
{  
    static void Main()  
    {  
        Trace.Msg("Now in Main...");  
        Console.WriteLine("Done.");  
    }  
}  
```  
  
 <span data-ttu-id="b0af6-171">Se o identificador `TRACE_ON` não estiver definido, nenhuma saída de rastreamento será exibida.</span><span class="sxs-lookup"><span data-stu-id="b0af6-171">If the `TRACE_ON` identifier is not defined, no trace output will be displayed.</span></span>  
  
 <span data-ttu-id="b0af6-172">O atributo `Conditional` é frequentemente usado com o identificador `DEBUG` para habilitar recursos de rastreamento e de registro em log para builds de depuração, mas não em builds de versão, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="b0af6-172">The `Conditional` attribute is often used with the `DEBUG` identifier to enable trace and logging features for debug builds but not in release builds, like this:</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
static void DebugMethod()  
{  
}  
```  
  
 <span data-ttu-id="b0af6-173">Quando um método marcado como condicional é chamado, a presença ou ausência do símbolo de pré-processamento especificado determina se a chamada será incluída ou omitida.</span><span class="sxs-lookup"><span data-stu-id="b0af6-173">When a method marked as conditional is called, the presence or absence of the specified preprocessing symbol determines whether the call is included or omitted.</span></span> <span data-ttu-id="b0af6-174">Se o símbolo estiver definido, a chamada será incluída, caso contrário, a chamada será omitida.</span><span class="sxs-lookup"><span data-stu-id="b0af6-174">If the symbol is defined, the call is included; otherwise, the call is omitted.</span></span> <span data-ttu-id="b0af6-175">O uso de `Conditional` é uma alternativa mais limpa, mais elegante e menos propensa a erros para incluir métodos dentro de blocos `#if…#endif`, dessa maneira:</span><span class="sxs-lookup"><span data-stu-id="b0af6-175">Using `Conditional` is a cleaner, more elegant, and less error-prone alternative to enclosing methods inside `#if…#endif` blocks, like this:</span></span>  
  
```csharp  
#if DEBUG  
    void ConditionalMethod()  
    {  
    }  
#endif  
```  
  
 <span data-ttu-id="b0af6-176">Um método condicional deve ser um método em uma declaração de classe ou de struct e não deve ter um valor retornado.</span><span class="sxs-lookup"><span data-stu-id="b0af6-176">A conditional method must be a method in a class or struct declaration and must not have a return value.</span></span>  
  
### <a name="using-multiple-identifiers"></a><span data-ttu-id="b0af6-177">Usando vários identificadores</span><span class="sxs-lookup"><span data-stu-id="b0af6-177">Using Multiple Identifiers</span></span>  
 <span data-ttu-id="b0af6-178">Se um método tem vários atributos `Conditional`, uma chamada para o método será incluída se pelo menos um dos símbolos condicionais for definido (em outras palavras, os símbolos são logicamente vinculados através do uso do operador OR).</span><span class="sxs-lookup"><span data-stu-id="b0af6-178">If a method has multiple `Conditional` attributes, a call to the method is included if at least one of the conditional symbols is defined (in other words, the symbols are logically linked together by using the OR operator).</span></span> <span data-ttu-id="b0af6-179">Neste exemplo, a presença de `A` ou `B` resultará em uma chamada de método:</span><span class="sxs-lookup"><span data-stu-id="b0af6-179">In this example, the presence of either `A` or `B` will result in a method call:</span></span>  
  
```csharp  
[Conditional("A"), Conditional("B")]  
static void DoIfAorB()  
{  
    // ...  
}  
```  
  
 <span data-ttu-id="b0af6-180">Para alcançar o efeito da vinculação lógica de símbolos usando o operador AND, você pode definir métodos condicionais em série.</span><span class="sxs-lookup"><span data-stu-id="b0af6-180">To achieve the effect of logically linking symbols by using the AND operator, you can define serial conditional methods.</span></span> <span data-ttu-id="b0af6-181">Por exemplo, o segundo método abaixo será executado somente se `A` e `B` estiverem definidos:</span><span class="sxs-lookup"><span data-stu-id="b0af6-181">For example, the second method below will execute only if both `A` and `B` are defined:</span></span>  
  
```csharp
[Conditional("A")]  
static void DoIfA()  
{  
    DoIfAandB();  
}  
  
[Conditional("B")]  
static void DoIfAandB()  
{  
    // Code to execute when both A and B are defined...  
}  
```  
  
### <a name="using-conditional-with-attribute-classes"></a><span data-ttu-id="b0af6-182">Usando condicional com classes de atributos</span><span class="sxs-lookup"><span data-stu-id="b0af6-182">Using Conditional with Attribute Classes</span></span>  
 <span data-ttu-id="b0af6-183">O atributo `Conditional` também pode ser aplicado a uma definição de classe de atributos.</span><span class="sxs-lookup"><span data-stu-id="b0af6-183">The `Conditional` attribute can also be applied to an attribute class definition.</span></span> <span data-ttu-id="b0af6-184">Neste exemplo, o atributo personalizado `Documentation` só adicionará informações aos metadados se DEBUG estiver definido.</span><span class="sxs-lookup"><span data-stu-id="b0af6-184">In this example, the custom attribute `Documentation` will only add information to the metadata if DEBUG is defined.</span></span>  
  
```csharp  
[Conditional("DEBUG")]  
public class Documentation : System.Attribute  
{  
    string text;  
  
    public Documentation(string text)  
    {  
        this.text = text;  
    }  
}  
  
class SampleClass  
{  
    // This attribute will only be included if DEBUG is defined.  
    [Documentation("This method displays an integer.")]  
    static void DoWork(int i)  
    {  
        System.Console.WriteLine(i.ToString());  
    }  
}  
```  
  
##  <span data-ttu-id="b0af6-185"><a name="CallerInfo"></a> Atributos de informações do chamador</span><span class="sxs-lookup"><span data-stu-id="b0af6-185"><a name="CallerInfo"></a> Caller Info Attributes</span></span>  
 <span data-ttu-id="b0af6-186">Ao usar atributos de informações do chamador, você pode obter informações sobre o chamador de um método.</span><span class="sxs-lookup"><span data-stu-id="b0af6-186">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="b0af6-187">Você pode obter o caminho do arquivo do código-fonte, o número de linha no código-fonte e o nome do membro do chamador.</span><span class="sxs-lookup"><span data-stu-id="b0af6-187">You can obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span>  
  
 <span data-ttu-id="b0af6-188">Para obter informações do chamador do membro, você usa os atributos que são aplicados aos parâmetros opcionais.</span><span class="sxs-lookup"><span data-stu-id="b0af6-188">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="b0af6-189">Cada parâmetro opcional especifica um valor padrão.</span><span class="sxs-lookup"><span data-stu-id="b0af6-189">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="b0af6-190">A tabela a seguir lista os atributos de informações do chamador que são definidos no namespace de <xref:System.Runtime.CompilerServices?displayProperty=fullName>:</span><span class="sxs-lookup"><span data-stu-id="b0af6-190">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="b0af6-191">Atributo</span><span class="sxs-lookup"><span data-stu-id="b0af6-191">Attribute</span></span>|<span data-ttu-id="b0af6-192">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0af6-192">Description</span></span>|<span data-ttu-id="b0af6-193">Tipo</span><span class="sxs-lookup"><span data-stu-id="b0af6-193">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="b0af6-194">O caminho completo do arquivo de origem que contém o chamador.</span><span class="sxs-lookup"><span data-stu-id="b0af6-194">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="b0af6-195">Esse é o caminho em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="b0af6-195">This is the path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="b0af6-196">Número de linha no arquivo de origem do qual o método é chamado.</span><span class="sxs-lookup"><span data-stu-id="b0af6-196">Line number in the source file from which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="b0af6-197">Nome do método ou nome da propriedade do chamador.</span><span class="sxs-lookup"><span data-stu-id="b0af6-197">Method name or property name of the caller.</span></span> <span data-ttu-id="b0af6-198">Para obter mais informações, consulte [Informações do chamador (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b0af6-198">For more information, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>|`String`|  
  
 <span data-ttu-id="b0af6-199">Para obter mais informações sobre os atributos de informações do chamador, consulte [Informações do chamador (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="b0af6-199">For more information about the Caller Info attributes, see [Caller Information (C#)](../../../../csharp/programming-guide/concepts/caller-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0af6-200">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b0af6-200">See Also</span></span>  
 <span data-ttu-id="b0af6-201"><xref:System.Reflection></span><span class="sxs-lookup"><span data-stu-id="b0af6-201"><xref:System.Reflection></span></span>   
 <span data-ttu-id="b0af6-202"><xref:System.Attribute></span><span class="sxs-lookup"><span data-stu-id="b0af6-202"><xref:System.Attribute></span></span>   
 <span data-ttu-id="b0af6-203">[Guia de Programação em C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b0af6-203">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b0af6-204">[Atributos](https://msdn.microsoft.com/library/5x6cd29c) </span><span class="sxs-lookup"><span data-stu-id="b0af6-204">[Attributes](https://msdn.microsoft.com/library/5x6cd29c) </span></span>  
 <span data-ttu-id="b0af6-205">[Reflexão (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span><span class="sxs-lookup"><span data-stu-id="b0af6-205">[Reflection (C#)](../../../../csharp/programming-guide/concepts/reflection.md) </span></span>  
 [<span data-ttu-id="b0af6-206">Acessando atributos usando reflexão (C#)</span><span class="sxs-lookup"><span data-stu-id="b0af6-206">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)

