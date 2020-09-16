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
ms.openlocfilehash: 7e006adb86886d22ec08dc61fa092bf677b4da96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544733"
---
# <a name="provideroption-element"></a><span data-ttu-id="20557-102">Elemento \<providerOption></span><span class="sxs-lookup"><span data-stu-id="20557-102">\<providerOption> Element</span></span>
<span data-ttu-id="20557-103">Especifica os atributos de versão do compilador para um provedor de idioma.</span><span class="sxs-lookup"><span data-stu-id="20557-103">Specifies the compiler version attributes for a language provider.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<providerOption>**

## <a name="syntax"></a><span data-ttu-id="20557-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="20557-104">Syntax</span></span>  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="20557-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="20557-105">Attributes and Elements</span></span>  
 <span data-ttu-id="20557-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="20557-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="20557-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="20557-107">Attributes</span></span>  
  
|<span data-ttu-id="20557-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="20557-108">Attribute</span></span>|<span data-ttu-id="20557-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="20557-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="20557-110">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="20557-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="20557-111">Especifica o nome da opção; por exemplo, "CompilerVersion".</span><span class="sxs-lookup"><span data-stu-id="20557-111">Specifies the name of the option; for example, "CompilerVersion".</span></span>|  
|`value`|<span data-ttu-id="20557-112">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="20557-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="20557-113">Especifica o valor para a opção; por exemplo, "v 3.5".</span><span class="sxs-lookup"><span data-stu-id="20557-113">Specifies the value for the option; for example, "v3.5".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="20557-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="20557-114">Child Elements</span></span>  
 <span data-ttu-id="20557-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="20557-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="20557-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="20557-116">Parent Elements</span></span>  
  
|<span data-ttu-id="20557-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="20557-117">Element</span></span>|<span data-ttu-id="20557-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="20557-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="20557-119">\<configuration> Elementos</span><span class="sxs-lookup"><span data-stu-id="20557-119">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="20557-120">O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="20557-120">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="20557-121">\<system.codedom> Elementos</span><span class="sxs-lookup"><span data-stu-id="20557-121">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="20557-122">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="20557-122">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="20557-123">\<compilers> Elementos</span><span class="sxs-lookup"><span data-stu-id="20557-123">\<compilers> Element</span></span>](compilers-element.md)|<span data-ttu-id="20557-124">Contêiner para elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.</span><span class="sxs-lookup"><span data-stu-id="20557-124">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
|[<span data-ttu-id="20557-125">\<compiler> Elementos</span><span class="sxs-lookup"><span data-stu-id="20557-125">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="20557-126">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="20557-126">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20557-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="20557-127">Remarks</span></span>  
 <span data-ttu-id="20557-128">Nos provedores de código do .NET Framework versão 3,5, Modelo de Objeto do Documento de Código (CodeDOM) podem dar suporte a opções específicas do provedor usando o `<providerOption>` elemento.</span><span class="sxs-lookup"><span data-stu-id="20557-128">In the .NET Framework version 3.5, Code Document Object Model (CodeDOM) code providers can support provider-specific options by using the `<providerOption>` element.</span></span>  
  
 <span data-ttu-id="20557-129">O .NET Framework 3,5 inclui assemblies .NET Framework 2,0 atualizados e fornece novos assemblies da versão 3,5 que contêm novos tipos.</span><span class="sxs-lookup"><span data-stu-id="20557-129">The .NET Framework 3.5 includes updated .NET Framework 2.0 assemblies and provides new version 3.5 assemblies that contain new types.</span></span> <span data-ttu-id="20557-130">Os provedores de código do Microsoft C# e Visual Basic estão contidos em assemblies do .NET Framework 2,0, mas foram atualizados para dar suporte a compiladores da versão 3,5.</span><span class="sxs-lookup"><span data-stu-id="20557-130">The Microsoft C# and Visual Basic code providers are contained in .NET Framework 2.0 assemblies but have been updated to support version 3.5 compilers.</span></span> <span data-ttu-id="20557-131">Por padrão, os provedores de código atualizados geram código para compiladores da versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="20557-131">By default, the updated code providers generate code for version 2.0 compilers.</span></span> <span data-ttu-id="20557-132">Você pode usar o `<providerOption>` elemento para alterar a versão do compilador de destino para 3,5.</span><span class="sxs-lookup"><span data-stu-id="20557-132">You can use the `<providerOption>` element to change the target compiler version to 3.5.</span></span> <span data-ttu-id="20557-133">Para fazer isso, especifique "CompilerVersion" para o `name` atributo e "v 3.5" para o `value` atributo.</span><span class="sxs-lookup"><span data-stu-id="20557-133">To do this, specify "CompilerVersion" for the `name` attribute and "v3.5" for the `value` attribute.</span></span> <span data-ttu-id="20557-134">Você deve preceder o número de versão com um "v" minúsculo.</span><span class="sxs-lookup"><span data-stu-id="20557-134">You must precede the version number with a lower-case "v".</span></span>  
  
 <span data-ttu-id="20557-135">Você pode tornar a especificação de versão global adicionando o `<providerOption>` elemento ao .NET Framework 2,0 Machine.config ou ao arquivo de Web.config raiz.</span><span class="sxs-lookup"><span data-stu-id="20557-135">You can make the version specification global by adding the `<providerOption>` element to the .NET Framework 2.0 Machine.config or root Web.config file.</span></span> <span data-ttu-id="20557-136">Se você atualizar a versão padrão do compilador para 3,5 no arquivo Machine.config, poderá alterá-la de volta para 2,0 em uma base por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="20557-136">If you update the default compiler version to 3.5 in the Machine.config file, you can change it back to 2.0 on a per-application basis by using the `<providerOption>` element in the application configuration file.</span></span>  
  
 <span data-ttu-id="20557-137">Os implementadores do provedor de código do CodeDOM podem processar opções personalizadas fornecendo um construtor que usa um `providerOptions` parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="20557-137">CodeDOM code provider implementers can process custom options by providing a constructor that takes a `providerOptions` parameter of type <xref:System.Collections.Generic.IDictionary%602>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20557-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20557-138">Example</span></span>  
 <span data-ttu-id="20557-139">O exemplo a seguir demonstra como especificar que a versão 3,5 do provedor de código C# deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="20557-139">The following example demonstrates how to specify that version 3.5 of the C# code provider should be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="20557-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="20557-140">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="20557-141">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="20557-141">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="20557-142">\<compilers> Elementos</span><span class="sxs-lookup"><span data-stu-id="20557-142">\<compilers> Element</span></span>](compilers-element.md)
- [<span data-ttu-id="20557-143">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="20557-143">Specifying Fully Qualified Type Names</span></span>](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="20557-144">[Elemento do compilador para compiladores para compilação (esquema de configurações do ASP.NET)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="20557-144">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))</span></span>
