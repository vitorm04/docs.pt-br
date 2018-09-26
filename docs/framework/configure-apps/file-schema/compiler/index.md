---
title: Esquema de configurações de compilador e de provedor de linguagem
ms.date: 03/30/2017
helpviewer_keywords:
- configuration settings [.NET Framework], compilers
- compiler configuration elements, schema
- compiler configuration elements
- language providers
- compiler configuration settings, schema
- configuration schema [.NET Framework], compiler settings
- language providers, settings schema
- compiler configuration settings
ms.assetid: c020b139-8699-4f0d-9ac9-70d0c5b2a8c8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c64dd85103e818ae603435c1a3f80f76e672ac84
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196766"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="c47ca-102">Esquema de configurações de compilador e de provedor de linguagem</span><span class="sxs-lookup"><span data-stu-id="c47ca-102">Compiler and Language Provider Settings Schema</span></span>
<span data-ttu-id="c47ca-103">As configurações do compilador e do provedor de linguagem especificam os elementos de configuração do compilador para os provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c47ca-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="c47ca-104">Cada elemento de configuração do compilador especifica o nome do tipo de provedor de código, os parâmetros do compilador, os nomes de linguagens com suporte e as extensões de arquivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="c47ca-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
 <span data-ttu-id="c47ca-105">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c47ca-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="c47ca-106">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="c47ca-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="c47ca-107">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="c47ca-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
 [<span data-ttu-id="c47ca-108">Elemento \<configuration></span><span class="sxs-lookup"><span data-stu-id="c47ca-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c47ca-109">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="c47ca-109">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)  
  
 [<span data-ttu-id="c47ca-110">\<compilers></span><span class="sxs-lookup"><span data-stu-id="c47ca-110">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
  
 [<span data-ttu-id="c47ca-111">\<compiler></span><span class="sxs-lookup"><span data-stu-id="c47ca-111">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)  
  
|<span data-ttu-id="c47ca-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="c47ca-112">Element</span></span>|<span data-ttu-id="c47ca-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c47ca-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c47ca-114">\<system.codedom></span><span class="sxs-lookup"><span data-stu-id="c47ca-114">\<system.codedom></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="c47ca-115">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c47ca-115">Specifies compiler configuration settings for available language providers.</span></span>|  
|[<span data-ttu-id="c47ca-116">\<compilers></span><span class="sxs-lookup"><span data-stu-id="c47ca-116">\<compilers></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="c47ca-117">Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).</span><span class="sxs-lookup"><span data-stu-id="c47ca-117">Container for compiler configuration elements; contains zero or more [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elements.</span></span>|  
|[<span data-ttu-id="c47ca-118">\<compiler></span><span class="sxs-lookup"><span data-stu-id="c47ca-118">\<compiler></span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|<span data-ttu-id="c47ca-119">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="c47ca-119">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c47ca-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c47ca-120">Example</span></span>  
 <span data-ttu-id="c47ca-121">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="c47ca-121">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c47ca-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c47ca-122">See Also</span></span>  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [<span data-ttu-id="c47ca-123">Esquema de arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="c47ca-123">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="c47ca-124">\<compiler> Element</span><span class="sxs-lookup"><span data-stu-id="c47ca-124">\<compiler> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
