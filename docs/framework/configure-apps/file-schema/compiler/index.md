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
ms.openlocfilehash: 457e90c92530e04070575e42e3fc282ce45b3d03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153944"
---
# <a name="compiler-and-language-provider-settings-schema"></a><span data-ttu-id="fa6ef-102">Esquema de configurações de compilador e de provedor de linguagem</span><span class="sxs-lookup"><span data-stu-id="fa6ef-102">Compiler and Language Provider Settings Schema</span></span>

<span data-ttu-id="fa6ef-103">As configurações do compilador e do provedor de linguagem especificam os elementos de configuração do compilador para os provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-103">Compiler and language provider settings specify compiler configuration elements for available language providers.</span></span> <span data-ttu-id="fa6ef-104">Cada elemento de configuração do compilador especifica o nome do tipo de provedor de código, os parâmetros do compilador, os nomes de linguagens com suporte e as extensões de arquivo com suporte.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-104">Each compiler configuration element specifies the code provider type name, compiler parameters, supported language names, and supported file extensions.</span></span>  
  
<span data-ttu-id="fa6ef-105">O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="fa6ef-105">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="fa6ef-106">Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-106">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="fa6ef-107">Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-107">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compilers>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiler>**](compiler-element.md)
  
|<span data-ttu-id="fa6ef-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa6ef-108">Element</span></span>|<span data-ttu-id="fa6ef-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa6ef-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|<span data-ttu-id="fa6ef-110">Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-110">Specifies compiler configuration settings for available language providers.</span></span>|  
|[\<compilers>](compilers-element.md)|<span data-ttu-id="fa6ef-111">Contêiner para elementos de configuração do compilador; contém zero ou mais [\<compiler>](compiler-element.md) elementos.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-111">Container for compiler configuration elements; contains zero or more [\<compiler>](compiler-element.md) elements.</span></span>|  
|[\<compiler>](compiler-element.md)|<span data-ttu-id="fa6ef-112">Especifica os atributos de configuração do compilador para um provedor de linguagem.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-112">Specifies the compiler configuration attributes for a language provider.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fa6ef-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa6ef-113">Example</span></span>  

 <span data-ttu-id="fa6ef-114">O exemplo a seguir ilustra um elemento típico de configuração do compilador.</span><span class="sxs-lookup"><span data-stu-id="fa6ef-114">The following example illustrates a typical compiler configuration element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fa6ef-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="fa6ef-115">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="fa6ef-116">Esquema do arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="fa6ef-116">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fa6ef-117">\<compiler> Elementos</span><span class="sxs-lookup"><span data-stu-id="fa6ef-117">\<compiler> Element</span></span>](compiler-element.md)
