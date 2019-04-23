---
title: Elemento <system.codedom>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
ms.openlocfilehash: 0f47255bb4073007a847e4a8b85ccfd34100582b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101608"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="6681c-102">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="6681c-102">\<system.codedom> Element</span></span>
<span data-ttu-id="6681c-103">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="6681c-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="6681c-104">\<Configuração > elemento</span><span class="sxs-lookup"><span data-stu-id="6681c-104">\<configuration> Element</span></span>  
<span data-ttu-id="6681c-105">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="6681c-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6681c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6681c-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6681c-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6681c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6681c-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6681c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6681c-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="6681c-109">Attributes</span></span>  
 <span data-ttu-id="6681c-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6681c-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6681c-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6681c-111">Child Elements</span></span>  
  
|<span data-ttu-id="6681c-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="6681c-112">Element</span></span>|<span data-ttu-id="6681c-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="6681c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6681c-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="6681c-114">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="6681c-115">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="6681c-115">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6681c-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6681c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6681c-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6681c-117">Element</span></span>|<span data-ttu-id="6681c-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6681c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6681c-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6681c-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="6681c-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6681c-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6681c-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="6681c-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="6681c-122">.NET framework versão 2.0</span><span class="sxs-lookup"><span data-stu-id="6681c-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="6681c-123">O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém definições de configuração do compilador para provedores de linguagem instalados em um computador, além de provedores padrão que são instalados com o .NET Framework, como o <xref:Microsoft.CSharp.CSharpCodeProvider> e o <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="6681c-123">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="6681c-124">O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="6681c-124">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="6681c-125">Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="6681c-125">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6681c-126">Os desenvolvedores e fornecedores do compilador podem adicionar definições de configuração para o arquivo de configuração de máquina (Machine. config) para um novo <xref:System.CodeDom.Compiler.CodeDomProvider> implementação.</span><span class="sxs-lookup"><span data-stu-id="6681c-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6681c-127">Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente os provedores de linguagem padrão e de provedores de linguagem identificados pelos parâmetros de configuração do compilador em um computador.</span><span class="sxs-lookup"><span data-stu-id="6681c-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6681c-128">Nas versões do .NET Framework 1.0 e 1.1, o idioma padrão provedores fornecidos pelo .NET Framework são identificados na [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="6681c-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element.</span></span> <span data-ttu-id="6681c-129">O .NET Framework versão 2.0, os provedores de linguagem padrão não são identificados na [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento, mas podem ser enumerados usando o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> método.</span><span class="sxs-lookup"><span data-stu-id="6681c-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="6681c-130">Versões 1.0 e 1.1 do .NET framework</span><span class="sxs-lookup"><span data-stu-id="6681c-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="6681c-131">O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém as definições de configuração do compilador para provedores de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="6681c-131">The [\<system.codedom>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="6681c-132">O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="6681c-132">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span> <span data-ttu-id="6681c-133">Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="6681c-133">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="6681c-134">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6681c-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="6681c-135">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="6681c-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="6681c-136">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="6681c-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6681c-137">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="6681c-137">Configuration File</span></span>  
 <span data-ttu-id="6681c-138">Esse elemento pode ser usado no arquivo de configuração do computador e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6681c-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6681c-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6681c-139">Example</span></span>  
 <span data-ttu-id="6681c-140">O exemplo a seguir ilustra uma configuração típica do compilador.</span><span class="sxs-lookup"><span data-stu-id="6681c-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6681c-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6681c-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="6681c-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="6681c-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="6681c-143">Esquema de configurações de compilador e de provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="6681c-143">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)
- [<span data-ttu-id="6681c-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="6681c-144">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
