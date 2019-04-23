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
ms.openlocfilehash: 9c69ea7bf95b311a796ec29d90410a77b748c3c6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229778"
---
# <a name="provideroption-element"></a><span data-ttu-id="f0b84-102">\<providerOption > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-102">\<providerOption> Element</span></span>
<span data-ttu-id="f0b84-103">Especifica os atributos de versão do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="f0b84-103">Specifies the compiler version attributes for a language provider.</span></span>  
  
 <span data-ttu-id="f0b84-104">\<Elemento de configuração ></span><span class="sxs-lookup"><span data-stu-id="f0b84-104">\<configuration Element></span></span>  
<span data-ttu-id="f0b84-105">\<Elemento System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="f0b84-105">\<system.codedom Element></span></span>  
<span data-ttu-id="f0b84-106">\<compiladores de elemento ></span><span class="sxs-lookup"><span data-stu-id="f0b84-106">\<compilers Element></span></span>  
<span data-ttu-id="f0b84-107">\<compilador > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-107">\<compiler> Element</span></span>  
<span data-ttu-id="f0b84-108">\<providerOption > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-108">\<providerOption> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0b84-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0b84-109">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0b84-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f0b84-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0b84-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f0b84-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0b84-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f0b84-112">Attributes</span></span>  
  
|<span data-ttu-id="f0b84-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f0b84-113">Attribute</span></span>|<span data-ttu-id="f0b84-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0b84-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="f0b84-115">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f0b84-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="f0b84-116">Especifica o nome da opção. Por exemplo, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="f0b84-116">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="f0b84-117">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="f0b84-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="f0b84-118">Especifica o valor para a opção. Por exemplo, "v3.5".</span><span class="sxs-lookup"><span data-stu-id="f0b84-118">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0b84-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f0b84-119">Child Elements</span></span>  
 <span data-ttu-id="f0b84-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="f0b84-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0b84-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f0b84-121">Parent Elements</span></span>  
  
|<span data-ttu-id="f0b84-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-122">Element</span></span>|<span data-ttu-id="f0b84-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0b84-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0b84-124">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="f0b84-124">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="f0b84-125">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f0b84-125">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="f0b84-126">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-126">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="f0b84-127">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f0b84-127">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="f0b84-128">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-128">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="f0b84-129">Contêiner para elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.</span><span class="sxs-lookup"><span data-stu-id="f0b84-129">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="f0b84-130">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="f0b84-130">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="f0b84-131">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="f0b84-131">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0b84-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0b84-132">Remarks</span></span>  
 <span data-ttu-id="f0b84-133">No .NET Framework versão 3.5, provedores de código de Code Document Object Model (CodeDOM) podem dar suporte a opções específicas do provedor usando o `<providerOption>` elemento.</span><span class="sxs-lookup"><span data-stu-id="f0b84-133">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="f0b84-134">O .NET Framework 3.5 inclui assemblies do .NET Framework 2.0 atualizados e fornece novos assemblies da versão 3.5 que contêm os novos tipos.</span><span class="sxs-lookup"><span data-stu-id="f0b84-134">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="f0b84-135">Os provedores de código Microsoft c# e Visual Basic estão contidos em assemblies do .NET Framework 2.0, mas foram atualizados para dar suporte a compiladores versão 3.5.</span><span class="sxs-lookup"><span data-stu-id="f0b84-135">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="f0b84-136">Por padrão, os provedores de código atualizado geram código para compiladores versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="f0b84-136">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="f0b84-137">Você pode usar o `<providerOption>` elemento para alterar a versão do compilador de destino para 3.5.</span><span class="sxs-lookup"><span data-stu-id="f0b84-137">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="f0b84-138">Para fazer isso, especifique "CompilerVersion" para o `name` atributo e "v3.5" para o `value` atributo.</span><span class="sxs-lookup"><span data-stu-id="f0b84-138">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="f0b84-139">Você deve preceder o número de versão com um "v" em letras minúsculas.</span><span class="sxs-lookup"><span data-stu-id="f0b84-139">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="f0b84-140">Você pode tornar a especificação de versão global adicionando o `<providerOption>` elemento para o Machine. config do .NET Framework 2.0 ou o arquivo Web. config de raiz.</span><span class="sxs-lookup"><span data-stu-id="f0b84-140">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="f0b84-141">Se você atualizar a versão do compilador padrão para 3.5 no arquivo Machine. config, você pode alterá-lo para 2.0 em uma base por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f0b84-141">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="f0b84-142">Implementadores de provedor de código codeDOM podem processar opções personalizadas, fornecendo um construtor que usa um `providerOptions` parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="f0b84-142">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0b84-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f0b84-143">Example</span></span>  
 <span data-ttu-id="f0b84-144">O exemplo a seguir demonstra como especificar a versão 3.5 do provedor de código c# deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="f0b84-144">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0b84-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0b84-145">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f0b84-146">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f0b84-146">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="f0b84-147">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="f0b84-147">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [<span data-ttu-id="f0b84-148">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="f0b84-148">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="f0b84-149">[Elemento de compilador para compiladores para compilação (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f0b84-149">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
