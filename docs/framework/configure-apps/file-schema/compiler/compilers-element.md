---
title: '&lt;compiladores&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8ce303d33a83d972247609e5d02d16a4a57669ff
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083787"
---
# <a name="ltcompilersgt-element"></a><span data-ttu-id="8eada-102">&lt;compiladores&gt; elemento</span><span class="sxs-lookup"><span data-stu-id="8eada-102">&lt;compilers&gt; Element</span></span>
<span data-ttu-id="8eada-103">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="8eada-103">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>  
  
 <span data-ttu-id="8eada-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="8eada-104">\<configuration></span></span>  
<span data-ttu-id="8eada-105">\<System. CodeDom ></span><span class="sxs-lookup"><span data-stu-id="8eada-105">\<system.codedom></span></span>  
<span data-ttu-id="8eada-106">\<compiladores > elemento</span><span class="sxs-lookup"><span data-stu-id="8eada-106">\<compilers> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eada-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eada-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8eada-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8eada-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8eada-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8eada-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8eada-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="8eada-110">Attributes</span></span>  
 <span data-ttu-id="8eada-111">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8eada-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8eada-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8eada-112">Child Elements</span></span>  
  
|<span data-ttu-id="8eada-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eada-113">Element</span></span>|<span data-ttu-id="8eada-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eada-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eada-115">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="8eada-115">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="8eada-116">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="8eada-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8eada-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8eada-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8eada-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="8eada-118">Element</span></span>|<span data-ttu-id="8eada-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="8eada-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8eada-120">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="8eada-120">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="8eada-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8eada-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8eada-122">\<System. CodeDom > elemento</span><span class="sxs-lookup"><span data-stu-id="8eada-122">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="8eada-123">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="8eada-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eada-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eada-124">Remarks</span></span>  
 <span data-ttu-id="8eada-125">O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém as definições de configuração do compilador para provedores de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="8eada-125">The [\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="8eada-126">Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="8eada-126">Each [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="8eada-127">O .NET Framework define o compilador iniciais e as configurações do provedor de linguagem no arquivo de configuração do computador (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8eada-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="8eada-128">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8eada-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="8eada-129">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="8eada-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="8eada-130">Arquivo de Configuração</span><span class="sxs-lookup"><span data-stu-id="8eada-130">Configuration File</span></span>  
 <span data-ttu-id="8eada-131">Esse elemento pode ser usado no arquivo de configuração do computador e o arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8eada-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eada-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8eada-132">Example</span></span>  
 <span data-ttu-id="8eada-133">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="8eada-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8eada-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eada-134">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="8eada-135">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="8eada-135">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="8eada-136">Esquema de configurações de compilador e de provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="8eada-136">Compiler and Language Provider Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [<span data-ttu-id="8eada-137">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="8eada-137">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
