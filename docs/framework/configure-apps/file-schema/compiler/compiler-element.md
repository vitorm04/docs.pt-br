---
title: '&lt;compilador&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2ef50301a5188193cc13cd0e657f53593ef0d93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcompilergt-element"></a><span data-ttu-id="2bc33-102">&lt;compilador&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-102">&lt;compiler&gt; Element</span></span>
<span data-ttu-id="2bc33-103">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="2bc33-103">Specifies the compiler configuration attributes for a language provider.</span></span>  
  
 <span data-ttu-id="2bc33-104">\<Elemento de configuração ></span><span class="sxs-lookup"><span data-stu-id="2bc33-104">\<configuration Element></span></span>  
<span data-ttu-id="2bc33-105">\<Elemento System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="2bc33-105">\<system.codedom Element></span></span>  
<span data-ttu-id="2bc33-106">\<compiladores de elemento ></span><span class="sxs-lookup"><span data-stu-id="2bc33-106">\<compilers Element></span></span>  
<span data-ttu-id="2bc33-107">\<compilador > elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-107">\<compiler> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc33-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2bc33-108">Syntax</span></span>  
  
```xml  
<compiler  
  language="languageName[;...;...]"  
  extension="fileExtension[;...;...]"  
  type="typeName, assemblyName"  
  warningLevel="number"  
  compilerOptions="option1 option2"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bc33-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2bc33-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2bc33-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2bc33-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bc33-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2bc33-111">Attributes</span></span>  
  
|<span data-ttu-id="2bc33-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2bc33-112">Attribute</span></span>|<span data-ttu-id="2bc33-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc33-113">Description</span></span>|  
|---------------|-----------------|  
|`compilerOptions`|<span data-ttu-id="2bc33-114">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="2bc33-114">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2bc33-115">Especifica os argumentos adicionais específicas do compilador para compilação.</span><span class="sxs-lookup"><span data-stu-id="2bc33-115">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="2bc33-116">Os valores para o `compilerOptions` atributo normalmente são listados em um tópico de opções do compilador para o compilador.</span><span class="sxs-lookup"><span data-stu-id="2bc33-116">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span> <span data-ttu-id="2bc33-117">Na documentação do Visual Studio 2005, é possível localizar as opções para o compilador procure "opções de compilador" no índice.</span><span class="sxs-lookup"><span data-stu-id="2bc33-117">In the Visual Studio 2005 documentation, you can locate the options for the compiler by looking for "compiler options" in the index.</span></span>|  
|`extension`|<span data-ttu-id="2bc33-118">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2bc33-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="2bc33-119">Fornece uma lista separada por ponto e vírgula de extensões de nome de arquivo usado por arquivos de origem para o provedor do idioma.</span><span class="sxs-lookup"><span data-stu-id="2bc33-119">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="2bc33-120">Por exemplo, ".cs".</span><span class="sxs-lookup"><span data-stu-id="2bc33-120">For example, ".cs".</span></span>|  
|`language`|<span data-ttu-id="2bc33-121">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2bc33-121">Required attribute.</span></span><br /><br /> <span data-ttu-id="2bc33-122">Fornece uma lista separada por vírgulas de nomes de idiomas suportados pelo provedor de idioma.</span><span class="sxs-lookup"><span data-stu-id="2bc33-122">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="2bc33-123">Por exemplo, "c#;cs;csharp".</span><span class="sxs-lookup"><span data-stu-id="2bc33-123">For example, "c#;cs;csharp".</span></span>|  
|`type`|<span data-ttu-id="2bc33-124">Atributo obrigatório.</span><span class="sxs-lookup"><span data-stu-id="2bc33-124">Required attribute.</span></span><br /><br /> <span data-ttu-id="2bc33-125">Especifica o nome do tipo do provedor de idioma, incluindo o nome do assembly que contém a implementação de provedor.</span><span class="sxs-lookup"><span data-stu-id="2bc33-125">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="2bc33-126">O nome do tipo deve atender aos requisitos definidos na [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="2bc33-126">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`warningLevel`|<span data-ttu-id="2bc33-127">Atributo opcional.</span><span class="sxs-lookup"><span data-stu-id="2bc33-127">Optional attribute.</span></span><br /><br /> <span data-ttu-id="2bc33-128">Especifica o nível de aviso do compilador padrão; Determina o nível no qual o provedor do idioma trata avisos de compilação como erros.</span><span class="sxs-lookup"><span data-stu-id="2bc33-128">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bc33-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2bc33-129">Child Elements</span></span>  
  
|<span data-ttu-id="2bc33-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-130">Element</span></span>|<span data-ttu-id="2bc33-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc33-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc33-132">\<Opção > elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-132">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="2bc33-133">Especifica os atributos de versão do compilador para um provedor de idioma.</span><span class="sxs-lookup"><span data-stu-id="2bc33-133">Specifies compiler version attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bc33-134">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2bc33-134">Parent Elements</span></span>  
  
|<span data-ttu-id="2bc33-135">Elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-135">Element</span></span>|<span data-ttu-id="2bc33-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="2bc33-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc33-137">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="2bc33-137">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="2bc33-138">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bc33-138">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="2bc33-139">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-139">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="2bc33-140">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="2bc33-140">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="2bc33-141">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-141">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="2bc33-142">Contêiner de elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.</span><span class="sxs-lookup"><span data-stu-id="2bc33-142">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bc33-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="2bc33-143">Remarks</span></span>  
 <span data-ttu-id="2bc33-144">Cada `<compiler>` elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="2bc33-144">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="2bc33-145">O provedor estende o <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe para um idioma específico; o `<compiler>` elemento define o compilador e as configurações do gerador de código para o provedor do idioma.</span><span class="sxs-lookup"><span data-stu-id="2bc33-145">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>  
  
 <span data-ttu-id="2bc33-146">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2bc33-146">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="2bc33-147">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="2bc33-147">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="2bc33-148">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="2bc33-148">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 <span data-ttu-id="2bc33-149">Elementos de compilador no aplicativo ou arquivo de configuração Web podem suplementar ou substituir as configurações no arquivo de configuração da máquina.</span><span class="sxs-lookup"><span data-stu-id="2bc33-149">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="2bc33-150">Se mais de uma implementação de provedor é configurada para o mesmo nome do idioma ou a mesma extensão de arquivo, a última configuração correspondente substitui quaisquer provedores configurados anteriores para essa extensão de arquivo ou nome de idioma.</span><span class="sxs-lookup"><span data-stu-id="2bc33-150">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="2bc33-151">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="2bc33-151">Configuration File</span></span>  
 <span data-ttu-id="2bc33-152">Esse elemento pode ser usado no arquivo de configuração de máquina e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2bc33-152">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bc33-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2bc33-153">Example</span></span>  
 <span data-ttu-id="2bc33-154">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="2bc33-154">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bc33-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2bc33-155">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="2bc33-156">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="2bc33-156">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="2bc33-157">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="2bc33-157">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [<span data-ttu-id="2bc33-158">Especificando nomes de tipo totalmente qualificados</span><span class="sxs-lookup"><span data-stu-id="2bc33-158">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [<span data-ttu-id="2bc33-159">compilador elemento compiladores para compilação (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="2bc33-159">compiler Element for compilers for compilation (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
