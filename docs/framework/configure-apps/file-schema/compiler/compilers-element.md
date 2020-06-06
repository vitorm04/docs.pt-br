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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155408"
---
# <a name="compilers-element"></a><span data-ttu-id="f18a2-102">Elemento \<compilers></span><span class="sxs-lookup"><span data-stu-id="f18a2-102">\<compilers> Element</span></span>
<span data-ttu-id="f18a2-103">Contêiner para elementos de configuração do compilador; contém zero ou mais [\<compiler>](compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="f18a2-103">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<compilers>**

## <a name="syntax"></a><span data-ttu-id="f18a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f18a2-104">Syntax</span></span>  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18a2-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f18a2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f18a2-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f18a2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18a2-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="f18a2-107">Attributes</span></span>  
 <span data-ttu-id="f18a2-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f18a2-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f18a2-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f18a2-109">Child Elements</span></span>  
  
|<span data-ttu-id="f18a2-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="f18a2-110">Element</span></span>|<span data-ttu-id="f18a2-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="f18a2-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a2-112">\<compiler>Elementos</span><span class="sxs-lookup"><span data-stu-id="f18a2-112">\<compiler> Element</span></span>](compiler-element.md)|<span data-ttu-id="f18a2-113">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="f18a2-113">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f18a2-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f18a2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f18a2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="f18a2-115">Element</span></span>|<span data-ttu-id="f18a2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="f18a2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18a2-117">\<configuration>Elementos</span><span class="sxs-lookup"><span data-stu-id="f18a2-117">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="f18a2-118">O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f18a2-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="f18a2-119">\<system.codedom>Elementos</span><span class="sxs-lookup"><span data-stu-id="f18a2-119">\<system.codedom> Element</span></span>](system-codedom-element.md)|<span data-ttu-id="f18a2-120">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="f18a2-120">Specifies compiler configuration settings for available language providers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f18a2-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="f18a2-121">Remarks</span></span>  
 <span data-ttu-id="f18a2-122">O [\<compilers>](compilers-element.md) elemento contém os parâmetros de configuração do compilador para provedores de idiomas em um computador.</span><span class="sxs-lookup"><span data-stu-id="f18a2-122">The [\<compilers>](compilers-element.md) element contains the compiler configuration settings for language providers on a computer.</span></span> <span data-ttu-id="f18a2-123">Cada [\<compiler>](compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.</span><span class="sxs-lookup"><span data-stu-id="f18a2-123">Each [\<compiler>](compiler-element.md) element specifies the compiler configuration attributes for a specific language provider.</span></span>  
  
 <span data-ttu-id="f18a2-124">O .NET Framework define as configurações iniciais do compilador e do provedor de idiomas no arquivo de configuração da máquina (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f18a2-124">The .NET Framework defines the initial compiler and language provider settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="f18a2-125">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f18a2-125">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="f18a2-126">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="f18a2-126">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f18a2-127">Arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="f18a2-127">Configuration File</span></span>  
 <span data-ttu-id="f18a2-128">Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f18a2-128">This element can be used in the machine configuration file and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18a2-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f18a2-129">Example</span></span>  
 <span data-ttu-id="f18a2-130">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="f18a2-130">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f18a2-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="f18a2-131">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="f18a2-132">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="f18a2-132">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f18a2-133">Esquema de configurações de compilador e de provedor de linguagem</span><span class="sxs-lookup"><span data-stu-id="f18a2-133">Compiler and Language Provider Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f18a2-134">\<compiler>Elementos</span><span class="sxs-lookup"><span data-stu-id="f18a2-134">\<compiler> Element</span></span>](compiler-element.md)
