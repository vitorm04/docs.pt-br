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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155382"
---
# <a name="systemcodedom-element"></a><span data-ttu-id="a89f2-102">Elemento \<system.codedom></span><span class="sxs-lookup"><span data-stu-id="a89f2-102">\<system.codedom> Element</span></span>
<span data-ttu-id="a89f2-103">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="a89f2-103">Specifies compiler configuration settings for available language providers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a><span data-ttu-id="a89f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a89f2-104">Syntax</span></span>  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a89f2-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a89f2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a89f2-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a89f2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a89f2-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a89f2-107">Attributes</span></span>  
 <span data-ttu-id="a89f2-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a89f2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a89f2-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a89f2-109">Child Elements</span></span>  
  
|<span data-ttu-id="a89f2-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="a89f2-110">Element</span></span>|<span data-ttu-id="a89f2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89f2-111">Description</span></span>|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="a89f2-112">Contêiner para elementos de configuração do compilador; contém zero ou mais [\<compiler>](compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="a89f2-112">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a89f2-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a89f2-113">Parent Elements</span></span>  
  
|<span data-ttu-id="a89f2-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="a89f2-114">Element</span></span>|<span data-ttu-id="a89f2-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89f2-115">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="a89f2-116">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a89f2-116">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a89f2-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a89f2-117">Remarks</span></span>  
  
## <a name="net-framework-version-20"></a><span data-ttu-id="a89f2-118">.NET Framework versão 2,0</span><span class="sxs-lookup"><span data-stu-id="a89f2-118">.NET Framework Version 2.0</span></span>  
 <span data-ttu-id="a89f2-119">O [\<system.codedom>](system-codedom-element.md) elemento contém definições de configuração de compilador para provedores de idiomas instalados em um computador além dos provedores padrão que são instalados com o .NET Framework, como o <xref:Microsoft.CSharp.CSharpCodeProvider> e o <xref:Microsoft.VisualBasic.VBCodeProvider> .</span><span class="sxs-lookup"><span data-stu-id="a89f2-119">The [\<system.codedom>](system-codedom-element.md) element contains compiler configuration settings for language providers installed on a computer in addition to the default providers that are installed with the .NET Framework, such as the <xref:Microsoft.CSharp.CSharpCodeProvider> and the <xref:Microsoft.VisualBasic.VBCodeProvider>.</span></span> <span data-ttu-id="a89f2-120">O [\<compilers>](compilers-element.md) elemento contém zero ou mais [\<compiler>](compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="a89f2-120">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="a89f2-121">Cada [\<compiler>](compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="a89f2-121">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a89f2-122">Os desenvolvedores e fornecedores de compilador podem adicionar definições de configuração ao arquivo de configuração da máquina (Machine. config) para uma nova <xref:System.CodeDom.Compiler.CodeDomProvider> implementação.</span><span class="sxs-lookup"><span data-stu-id="a89f2-122">Developers and compiler vendors can add configuration settings to the machine configuration file (Machine.config) for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a89f2-123">Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente os provedores de idioma padrão e os provedores de idiomas identificados pelas definições de configuração do compilador em um computador.</span><span class="sxs-lookup"><span data-stu-id="a89f2-123">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate both the default language providers and language providers identified by the compiler configuration settings on a computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a89f2-124">No .NET Framework versões 1,0 e 1,1, os provedores de idioma padrão fornecidos pelo .NET Framework são identificados no [\<compilers>](compilers-element.md) elemento.</span><span class="sxs-lookup"><span data-stu-id="a89f2-124">In the .NET Framework versions 1.0 and 1.1, the default language providers supplied by the .NET Framework are identified in the [\<compilers>](compilers-element.md) element.</span></span> <span data-ttu-id="a89f2-125">No .NET Framework versão 2,0, os provedores de idioma padrão não são identificados no [\<compilers>](compilers-element.md) elemento, mas podem ser enumerados usando o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> método.</span><span class="sxs-lookup"><span data-stu-id="a89f2-125">In the .NET Framework version 2.0, the default language providers are not identified in the [\<compilers>](compilers-element.md) element, but can be enumerated using the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> method.</span></span>  
  
## <a name="net-framework-versions-10-and-11"></a><span data-ttu-id="a89f2-126">.NET Framework versões 1,0 e 1,1</span><span class="sxs-lookup"><span data-stu-id="a89f2-126">.NET Framework Versions 1.0 and 1.1</span></span>  
 <span data-ttu-id="a89f2-127">O [\<system.codedom>](system-codedom-element.md) elemento contém os parâmetros de configuração do compilador para provedores de idiomas em um computador.</span><span class="sxs-lookup"><span data-stu-id="a89f2-127">The [\<system.codedom>](system-codedom-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="a89f2-128">O [\<compilers>](compilers-element.md) elemento contém zero ou mais [\<compiler>](compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="a89f2-128">The [\<compilers>](compilers-element.md) element contains zero or more [\<compiler>](compiler-element.md) elements.</span></span> <span data-ttu-id="a89f2-129">Cada [\<compiler>](compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="a89f2-129">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="a89f2-130">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a89f2-130">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="a89f2-131">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="a89f2-131">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="a89f2-132">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="a89f2-132">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="a89f2-133">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="a89f2-133">Configuration File</span></span>  
 <span data-ttu-id="a89f2-134">Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a89f2-134">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a89f2-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a89f2-135">Example</span></span>  
 <span data-ttu-id="a89f2-136">O exemplo a seguir ilustra uma configuração de compilador típica.</span><span class="sxs-lookup"><span data-stu-id="a89f2-136">The following example illustrates a typical compiler configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a89f2-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="a89f2-137">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="a89f2-138">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="a89f2-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a89f2-139">Esquema de configurações de compilador e de provedor de linguagem</span><span class="sxs-lookup"><span data-stu-id="a89f2-139">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a89f2-140">\<compiler>Elementos</span><span class="sxs-lookup"><span data-stu-id="a89f2-140">\<compiler> Element</span></span>](compiler-element.md)
