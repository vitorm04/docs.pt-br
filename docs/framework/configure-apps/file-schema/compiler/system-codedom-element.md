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
ms.openlocfilehash: 43bc3c40bfc0b0ce4c0b18683092faf8b67e1c04
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927690"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="b81d4-102">\<Elemento de > System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="b81d4-102">\<system.codedom> Element</span></span>
<span data-ttu-id="b81d4-103">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="b81d4-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
 <span data-ttu-id="b81d4-104">\<Elemento de > de configuração</span><span class="sxs-lookup"><span data-stu-id="b81d4-104">\<configuration> Element</span></span>  
<span data-ttu-id="b81d4-105">\<Elemento de > System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="b81d4-105">\<system.codedom> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b81d4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b81d4-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b81d4-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b81d4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="b81d4-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b81d4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b81d4-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="b81d4-109">Attributes</span></span>  
 <span data-ttu-id="b81d4-110">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b81d4-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b81d4-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b81d4-111">Child Elements</span></span>  
  
|<span data-ttu-id="b81d4-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="b81d4-112">Element</span></span>|<span data-ttu-id="b81d4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="b81d4-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b81d4-114">\<compilers></span><span class="sxs-lookup"><span data-stu-id="b81d4-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="b81d4-115">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="b81d4-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b81d4-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b81d4-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b81d4-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b81d4-117">Element</span></span>|<span data-ttu-id="b81d4-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b81d4-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b81d4-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b81d4-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="b81d4-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b81d4-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b81d4-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="b81d4-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="b81d4-122">.NET Framework versão 2,0</span><span class="sxs-lookup"><span data-stu-id="b81d4-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="b81d4-123"><xref:Microsoft.CSharp.CSharpCodeProvider> O [ \<elemento System. CodeDom >](system-codedom-element.md) contém definições de configuração de compilador para provedores de idiomas instalados em um computador além dos provedores padrão instalados com o .NET Framework, como o e o <xref:Microsoft.VisualBasic.VBCodeProvider>.</span><span class="sxs-lookup"><span data-stu-id="b81d4-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="b81d4-124">O elemento [ \<>](compilers-element.md) de compiladores contém zero ou mais [ \<](compiler-element.md) elementos de > do compilador.</span><span class="sxs-lookup"><span data-stu-id="b81d4-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="b81d4-125">Cada elemento > do compilador Especifica os atributos de configuração do compilador para um provedor de idioma específico. [ \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="b81d4-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b81d4-126">Os desenvolvedores e fornecedores de compilador podem adicionar definições de configuração ao arquivo de configuração da máquina (Machine. config <xref:System.CodeDom.Compiler.CodeDomProvider> ) para uma nova implementação.</span><span class="sxs-lookup"><span data-stu-id="b81d4-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="b81d4-127">Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente os provedores de idioma padrão e os provedores de idiomas identificados pelas definições de configuração do compilador em um computador.</span><span class="sxs-lookup"><span data-stu-id="b81d4-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b81d4-128">No .NET Framework versões 1,0 e 1,1, os provedores de idioma padrão fornecidos pelo .NET Framework são identificados no [ \<elemento compiladores >](compilers-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b81d4-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="b81d4-129">No .NET Framework versão 2,0, os provedores de idioma padrão não são identificados no <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> [ \<elemento compiladores >](compilers-element.md) , mas podem ser enumerados usando o método.</span><span class="sxs-lookup"><span data-stu-id="b81d4-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="b81d4-130">.NET Framework versões 1,0 e 1,1</span><span class="sxs-lookup"><span data-stu-id="b81d4-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="b81d4-131">O elemento System [. CodeDom > contém as definições de configuração do compilador para os provedores de idioma em um computador. \<](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="b81d4-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="b81d4-132">O elemento [ \<>](compilers-element.md) de compiladores contém zero ou mais [ \<](compiler-element.md) elementos de > do compilador.</span><span class="sxs-lookup"><span data-stu-id="b81d4-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="b81d4-133">Cada elemento > do compilador Especifica os atributos de configuração do compilador para um provedor de idioma específico. [ \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="b81d4-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="b81d4-134">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b81d4-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="b81d4-135">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="b81d4-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="b81d4-136">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="b81d4-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b81d4-137">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="b81d4-137">Configuration File</span></span>  
 <span data-ttu-id="b81d4-138">Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b81d4-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b81d4-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b81d4-139">Example</span></span>  
 <span data-ttu-id="b81d4-140">O exemplo a seguir ilustra uma configuração de compilador típica.</span><span class="sxs-lookup"><span data-stu-id="b81d4-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b81d4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b81d4-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="b81d4-142">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="b81d4-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b81d4-143">Esquema de configurações de compilador e de provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="b81d4-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b81d4-144">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="b81d4-144">\<compiler> Element</span></span>](compiler-element.md)
