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
ms.openlocfilehash: a651e4ca76fda9e65ea4a5848c19b1f0ebfe91b1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168926"
---
# <a name="compiler-and-language-provider-settings-schema"></a>Esquema de configurações de compilador e de provedor de linguagem
As configurações do compilador e do provedor de linguagem especificam os elementos de configuração do compilador para os provedores de linguagem disponíveis. Cada elemento de configuração do compilador especifica o nome do tipo de provedor de código, os parâmetros do compilador, os nomes de linguagens com suporte e as extensões de arquivo com suporte.  
  
O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<> System. CodeDom**](system-codedom-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<compiladores >** ](compilers-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do compilador**](compiler-element.md)  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<system.codedom>](system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
|[\<compilers>](compilers-element.md)|Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](compiler-element.md).|  
|[\<compiler>](compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra um elemento típico de configuração do compilador.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Esquema de arquivos de configuração](../index.md)
- [\<compiler> Element](compiler-element.md)
