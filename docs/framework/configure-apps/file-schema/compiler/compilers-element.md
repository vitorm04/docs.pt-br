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
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155408"
---
# <a name="compilers-element"></a><span data-ttu-id="fb2d9-102">\<compiladores> Element</span><span class="sxs-lookup"><span data-stu-id="fb2d9-102">\<compilers> Element</span></span>
<span data-ttu-id="fb2d9-103">Recipiente para elementos de configuração do compilador; contém elementos>com [ \<compilador](compiler-element.md) zero ou mais.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

<span data-ttu-id="fb2d9-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb2d9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fb2d9-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span><span class="sxs-lookup"><span data-stu-id="fb2d9-105">&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)</span></span>\
<span data-ttu-id="fb2d9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compiladores>**</span><span class="sxs-lookup"><span data-stu-id="fb2d9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fb2d9-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb2d9-107">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb2d9-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fb2d9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fb2d9-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb2d9-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="fb2d9-110">Attributes</span></span>  
 <span data-ttu-id="fb2d9-111">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fb2d9-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fb2d9-112">Child Elements</span></span>  
  
|<span data-ttu-id="fb2d9-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb2d9-113">Element</span></span>|<span data-ttu-id="fb2d9-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb2d9-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb2d9-115">\<elemento> compilador</span><span class="sxs-lookup"><span data-stu-id="fb2d9-115">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="fb2d9-116">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-116">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb2d9-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fb2d9-117">Parent Elements</span></span>  
  
|<span data-ttu-id="fb2d9-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="fb2d9-118">Element</span></span>|<span data-ttu-id="fb2d9-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="fb2d9-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb2d9-120">\<elemento> de configuração</span><span class="sxs-lookup"><span data-stu-id="fb2d9-120">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="fb2d9-121">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="fb2d9-122">\<system.codedom> Element</span><span class="sxs-lookup"><span data-stu-id="fb2d9-122">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="fb2d9-123">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-123">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb2d9-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="fb2d9-124">Remarks</span></span>  
 <span data-ttu-id="fb2d9-125">Os [ \<compiladores>](compilers-element.md) elemento contém as configurações de configuração do compilador para provedores de idiomas em um computador.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-125">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="fb2d9-126">Cada [ \<compilador>](compiler-element.md) elemento especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-126">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="fb2d9-127">O .NET Framework define as configurações iniciais do compilador e do provedor de idiomas no arquivo de configuração da máquina (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fb2d9-127">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="fb2d9-128">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-128">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fb2d9-129">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-129">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="fb2d9-130">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="fb2d9-130">Configuration File</span></span>  
 <span data-ttu-id="fb2d9-131">Este elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-131">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2d9-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb2d9-132">Example</span></span>  
 <span data-ttu-id="fb2d9-133">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="fb2d9-133">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fb2d9-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb2d9-134">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="fb2d9-135">Esquema de arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="fb2d9-135">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fb2d9-136">Esquema de configurações do compilador e do provedor de idiomas</span><span class="sxs-lookup"><span data-stu-id="fb2d9-136">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fb2d9-137">\<elemento> compilador</span><span class="sxs-lookup"><span data-stu-id="fb2d9-137">\<compiler> Element</span></span>](compiler-element.md)
