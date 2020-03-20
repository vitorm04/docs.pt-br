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
ms.openlocfilehash: 40a3c84e1deed4d215383670176623a6a79ac41d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155382"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="932fc-102">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="932fc-102">\<system.codedom> Element</span></span>
<span data-ttu-id="932fc-103">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="932fc-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[<span data-ttu-id="932fc-104">**\<>de configuração**</span><span class="sxs-lookup"><span data-stu-id="932fc-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="932fc-105">&nbsp;&nbsp;**\<system.codedom>**</span><span class="sxs-lookup"><span data-stu-id="932fc-105">&nbsp;&nbsp;**\<system.codedom>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="932fc-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="932fc-106">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="932fc-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="932fc-107">Attributes and Elements</span></span>  
 <span data-ttu-id="932fc-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="932fc-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="932fc-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="932fc-109">Attributes</span></span>  
 <span data-ttu-id="932fc-110">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="932fc-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="932fc-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="932fc-111">Child Elements</span></span>  
  
|<span data-ttu-id="932fc-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="932fc-112">Element</span></span>|<span data-ttu-id="932fc-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="932fc-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="932fc-114">\<compiladores></span><span class="sxs-lookup"><span data-stu-id="932fc-114">\<compilers></span></span>](compilers-element.md)|<span data-ttu-id="932fc-115">Recipiente para elementos de configuração do compilador; contém elementos>com [ \<compilador](compiler-element.md) zero ou mais.</span><span class="sxs-lookup"><span data-stu-id="932fc-115">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="932fc-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="932fc-116">Parent Elements</span></span>  
  
|<span data-ttu-id="932fc-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="932fc-117">Element</span></span>|<span data-ttu-id="932fc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="932fc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="932fc-119">\<>de configuração</span><span class="sxs-lookup"><span data-stu-id="932fc-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="932fc-120">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="932fc-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="932fc-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="932fc-121">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="932fc-122">.NET Framework Versão 2.0</span><span class="sxs-lookup"><span data-stu-id="932fc-122">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="932fc-123"><xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>O [ \<elemento system.codedom>](system-codedom-element.md) contém configurações de configuração do compilador para provedores de idiomainstalados em um computador, além dos provedores padrão que estão instalados com o .NET Framework, como o e o .</span><span class="sxs-lookup"><span data-stu-id="932fc-123">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="932fc-124">Os [ \<compiladores>](compilers-element.md) elemento contém elementos>zero ou mais [ \<compilador.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="932fc-124">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="932fc-125">Cada [ \<compilador>](compiler-element.md) elemento especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="932fc-125">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="932fc-126">Desenvolvedores e fornecedores de compiladores podem adicionar configurações ao arquivo de <xref:System.CodeDom.Compiler.CodeDomProvider> configuração da máquina (Machine.config) para uma nova implementação.</span><span class="sxs-lookup"><span data-stu-id="932fc-126">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="932fc-127">Use <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> o método para enumerar de forma programática tanto os provedores de idiomas padrão quanto os provedores de idiomas identificados pelas configurações de configuração do compilador em um computador.</span><span class="sxs-lookup"><span data-stu-id="932fc-127">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="932fc-128">Nas versões .NET Framework 1.0 e 1.1, os provedores de linguagem padrão fornecidos pelo .NET Framework são identificados no elemento [ \<>compiladores.](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="932fc-128">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="932fc-129">Na versão 2.0 do .NET Framework, os provedores de linguagem padrão não são identificados <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> nos [ \<compiladores>](compilers-element.md) elemento, mas podem ser enumerados usando o método.</span><span class="sxs-lookup"><span data-stu-id="932fc-129">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="932fc-130">.NET Framework Versões 1.0 e 1.1</span><span class="sxs-lookup"><span data-stu-id="932fc-130">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="932fc-131">O elemento [ \<system.codedom>](system-codedom-element.md) contém as configurações de configuração do compilador para provedores de idiomas em um computador.</span><span class="sxs-lookup"><span data-stu-id="932fc-131">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="932fc-132">Os [ \<compiladores>](compilers-element.md) elemento contém elementos>zero ou mais [ \<compilador.](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="932fc-132">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="932fc-133">Cada [ \<compilador>](compiler-element.md) elemento especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="932fc-133">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="932fc-134">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="932fc-134">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="932fc-135">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="932fc-135">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="932fc-136">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="932fc-136">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="932fc-137">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="932fc-137">Configuration File</span></span>  
 <span data-ttu-id="932fc-138">Este elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="932fc-138">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="932fc-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="932fc-139">Example</span></span>  
 <span data-ttu-id="932fc-140">O exemplo a seguir ilustra uma configuração típica do compilador.</span><span class="sxs-lookup"><span data-stu-id="932fc-140">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="932fc-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="932fc-141">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="932fc-142">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="932fc-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="932fc-143">Esquema de configurações do compilador e do provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="932fc-143">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="932fc-144">\<elemento> compilador</span><span class="sxs-lookup"><span data-stu-id="932fc-144">\<compiler> Element</span></span>](compiler-element.md)
