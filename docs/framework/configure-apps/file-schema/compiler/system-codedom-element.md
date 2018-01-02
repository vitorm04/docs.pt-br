---
title: '&lt;System. CodeDom&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
caps.latest.revision: "17"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bf2e041f9ae9661a9b6f8ecd5883ac7d1b0f0dec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemcodedomgt-element"></a><span data-ttu-id="55d49-102">&lt;System. CodeDom&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="55d49-102">&lt;system.codedom&gt; Element</span></span>
<span data-ttu-id="55d49-103">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="55d49-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="55d49-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="55d49-104">\<configuration> Element</span></span>  
<span data-ttu-id="55d49-105">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="55d49-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55d49-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55d49-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55d49-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="55d49-107">Attributes and Elements</span></span>  
 <span data-ttu-id="55d49-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="55d49-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55d49-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="55d49-109">Attributes</span></span>  
 <span data-ttu-id="55d49-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="55d49-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55d49-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="55d49-111">Child Elements</span></span>  
  
|<span data-ttu-id="55d49-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="55d49-112">Element</span></span>|<span data-ttu-id="55d49-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="55d49-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55d49-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="55d49-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="55d49-115">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="55d49-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55d49-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="55d49-116">Parent Elements</span></span>  
  
|<span data-ttu-id="55d49-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="55d49-117">Element</span></span>|<span data-ttu-id="55d49-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="55d49-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55d49-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="55d49-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="55d49-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55d49-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55d49-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="55d49-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="55d49-122">.NET framework versão 2.0</span><span class="sxs-lookup"><span data-stu-id="55d49-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="55d49-123">O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém definições de configuração do compilador para provedores de idioma instalados em um computador, além dos provedores padrão que são instalados com o .NET Framework, como o <xref:Microsoft.CSharp.CSharpCodeProvider> e <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="55d49-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="55d49-124">O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="55d49-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="55d49-125">Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="55d49-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="55d49-126">Os desenvolvedores e fornecedores de compilador podem adicionar parâmetros de configuração para o arquivo de configuração de máquina (Machine. config) para um novo <xref:System.CodeDom.Compiler.CodeDomProvider> implementação.</span><span class="sxs-lookup"><span data-stu-id="55d49-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="55d49-127">Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente a provedores de idioma padrão e os provedores de linguagem identificados pelos parâmetros de configuração do compilador em um computador.</span><span class="sxs-lookup"><span data-stu-id="55d49-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55d49-128">Nas versões do .NET Framework 1.0 e 1.1, o idioma padrão provedores fornecidos pelo .NET Framework são identificados no [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="55d49-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="55d49-129">O .NET Framework versão 2.0, os provedores de idioma padrão não são identificados no [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento, mas podem ser enumerados usando o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> método.</span><span class="sxs-lookup"><span data-stu-id="55d49-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="55d49-130">Versões 1.0 e 1.1 do .NET framework</span><span class="sxs-lookup"><span data-stu-id="55d49-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="55d49-131">O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém as definições de configuração do compilador para provedores de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="55d49-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="55d49-132">O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="55d49-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="55d49-133">Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="55d49-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="55d49-134">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="55d49-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="55d49-135">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="55d49-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="55d49-136">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="55d49-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="55d49-137">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="55d49-137">Configuration File</span></span>  
 <span data-ttu-id="55d49-138">Esse elemento pode ser usado no arquivo de configuração de máquina e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="55d49-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d49-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55d49-139">Example</span></span>  
 <span data-ttu-id="55d49-140">O exemplo a seguir ilustra uma configuração típica do compilador.</span><span class="sxs-lookup"><span data-stu-id="55d49-140">The following example illustrates a typical compiler configuration.</span></span>  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler   
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=1.0.5000.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions=""  
        warningLevel="1" />  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="55d49-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55d49-141">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="55d49-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="55d49-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="55d49-143">Esquema de configurações de compilador e de provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="55d49-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="55d49-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="55d49-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
