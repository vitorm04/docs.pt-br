---
title: Elemento <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155395"
---
# <a name="provideroption-element"></a><span data-ttu-id="dfaa6-102">\<providerOpção> Elemento</span><span class="sxs-lookup"><span data-stu-id="dfaa6-102">\<providerOption> Element</span></span>
<span data-ttu-id="dfaa6-103">Especifica os atributos da versão do compilador para um provedor de idiomas.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-103">Specifies the compiler version attributes for a language provider.</span></span>  

<span data-ttu-id="dfaa6-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfaa6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dfaa6-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfaa6-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="dfaa6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiladores>**](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfaa6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)</span></span>\
<span data-ttu-id="dfaa6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>do compilador**](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="dfaa6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)</span></span>\
<span data-ttu-id="dfaa6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<provedorOpção>**</span><span class="sxs-lookup"><span data-stu-id="dfaa6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**</span></span>

## <a name="syntax"></a><span data-ttu-id="dfaa6-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dfaa6-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dfaa6-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dfaa6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dfaa6-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dfaa6-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="dfaa6-112">Attributes</span></span>  
  
|<span data-ttu-id="dfaa6-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="dfaa6-113">Attribute</span></span>|<span data-ttu-id="dfaa6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfaa6-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="dfaa6-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="dfaa6-116">Especifica o nome da opção; por exemplo, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="dfaa6-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="dfaa6-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="dfaa6-118">Especifica o valor da opção; por exemplo, "v3.5".</span><span class="sxs-lookup"><span data-stu-id="dfaa6-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dfaa6-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dfaa6-119">Child Elements</span></span>  
 <span data-ttu-id="dfaa6-120">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dfaa6-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dfaa6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="dfaa6-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfaa6-122">Element</span></span>|<span data-ttu-id="dfaa6-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="dfaa6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dfaa6-124">\<elemento> de configuração</span><span class="sxs-lookup"><span data-stu-id="dfaa6-124">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="dfaa6-125">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="dfaa6-126">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="dfaa6-126">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="dfaa6-127">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="dfaa6-128">\<compiladores> Element</span><span class="sxs-lookup"><span data-stu-id="dfaa6-128">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="dfaa6-129">Recipiente para elementos de configuração do compilador; contém zero `<compiler>` ou mais elementos.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="dfaa6-130">\<elemento> compilador</span><span class="sxs-lookup"><span data-stu-id="dfaa6-130">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="dfaa6-131">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfaa6-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="dfaa6-132">Remarks</span></span>  
 <span data-ttu-id="dfaa6-133">Na versão 3.5 do .NET Framework, os provedores de código Code Document Object `<providerOption>` Model (CodeDOM) podem suportar opções específicas do provedor usando o elemento.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="dfaa6-134">O .NET Framework 3.5 inclui conjuntos atualizados do .NET Framework 2.0 e fornece novas montagens de versão 3.5 que contêm novos tipos.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="dfaa6-135">Os provedores de código Microsoft C# e Visual Basic estão contidos em conjuntos .NET Framework 2.0, mas foram atualizados para suportar compiladores da versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="dfaa6-136">Por padrão, os provedores de código atualizados geram código para compiladores da versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="dfaa6-137">Você pode `<providerOption>` usar o elemento para alterar a versão do compilador de destino para 3.5.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="dfaa6-138">Para fazer isso, especifique "CompilerVersion" para o `name` `value` atributo e "v3.5" para o atributo.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="dfaa6-139">Você deve preceder o número da versão com um "v" minúsculo.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="dfaa6-140">Você pode tornar a especificação `<providerOption>` da versão global adicionando o elemento ao arquivo .NET Framework 2.0 Machine.config ou root Web.config.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="dfaa6-141">Se você atualizar a versão do compilador padrão para 3.5 no arquivo Machine.config, você poderá alterá-la de volta para 2.0 por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="dfaa6-142">Os implementadores do provedor de código CodeDOM podem `providerOptions` processar opções personalizadas fornecendo um construtor que leva um parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfaa6-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="dfaa6-143">Example</span></span>  
 <span data-ttu-id="dfaa6-144">O exemplo a seguir demonstra como especificar que a versão 3.5 do provedor de código C# deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="dfaa6-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dfaa6-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="dfaa6-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="dfaa6-146">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="dfaa6-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="dfaa6-147">\<compiladores> Element</span><span class="sxs-lookup"><span data-stu-id="dfaa6-147">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="dfaa6-148">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="dfaa6-148">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="dfaa6-149">[elemento compilador para compiladores para compilação (ASP.NET Configurações Esquema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dfaa6-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
