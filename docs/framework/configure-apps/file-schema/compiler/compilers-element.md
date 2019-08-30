---
title: Elemento <compilers>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 5232c5bd2d4fad8104d156bfa86141ceb7f0dd93
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167699"
---
# <a name="compilers-element"></a><span data-ttu-id="fd70f-102">\<compilador > elemento</span><span class="sxs-lookup"><span data-stu-id="fd70f-102">\<compilers> Element</span></span>
<span data-ttu-id="fd70f-103">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="fd70f-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  
  
[<span data-ttu-id="fd70f-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="fd70f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="fd70f-105">&nbsp;&nbsp;[ **\<> System. CodeDom**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd70f-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>  
<span data-ttu-id="fd70f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<compiladores >**</span><span class="sxs-lookup"><span data-stu-id="fd70f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd70f-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fd70f-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd70f-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fd70f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fd70f-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fd70f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd70f-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fd70f-110">Attributes</span></span>  
 <span data-ttu-id="fd70f-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fd70f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fd70f-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fd70f-112">Child Elements</span></span>  
  
|<span data-ttu-id="fd70f-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fd70f-113">Element</span></span>|<span data-ttu-id="fd70f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd70f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd70f-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="fd70f-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="fd70f-116">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="fd70f-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd70f-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fd70f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fd70f-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="fd70f-118">Element</span></span>|<span data-ttu-id="fd70f-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fd70f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd70f-120">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="fd70f-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="fd70f-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd70f-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="fd70f-122">\<Elemento de > System. CodeDom</span><span class="sxs-lookup"><span data-stu-id="fd70f-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="fd70f-123">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fd70f-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd70f-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="fd70f-124">Remarks</span></span>  
 <span data-ttu-id="fd70f-125">O elemento > de compiladores contém os parâmetros de configuração do compilador para provedores de idiomas em um computador. [ \<](compilers-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd70f-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="fd70f-126">Cada elemento > do compilador Especifica os atributos de configuração do compilador para um provedor de idioma específico. [ \<](compiler-element.md)</span><span class="sxs-lookup"><span data-stu-id="fd70f-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="fd70f-127">O .NET Framework define as configurações iniciais do compilador e do provedor de idiomas no arquivo de configuração da máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="fd70f-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="fd70f-128">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fd70f-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fd70f-129">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="fd70f-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fd70f-130">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="fd70f-130">Configuration File</span></span>  
 <span data-ttu-id="fd70f-131">Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fd70f-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd70f-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd70f-132">Example</span></span>  
 <span data-ttu-id="fd70f-133">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="fd70f-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler   
          language="c#;cs;csharp"   
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""    
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd70f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd70f-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="fd70f-135">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="fd70f-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fd70f-136">Esquema de configurações de compilador e de provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="fd70f-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd70f-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="fd70f-137">\<compiler> Element</span></span>](compiler-element.md)
