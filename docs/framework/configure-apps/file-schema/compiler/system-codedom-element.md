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
# <a name="systemcodedom-element"></a>\<system.codedom> Element
Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.  
  
[**\<>de configuração**](../configuration-element.md)  
&nbsp;&nbsp;**\<system.codedom>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<compiladores>](compilers-element.md)|Recipiente para elementos de configuração do compilador; contém elementos>com [ \<compilador](compiler-element.md) zero ou mais.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de configuração](../configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="net-framework-version-20"></a>.NET Framework Versão 2.0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> <xref:Microsoft.VisualBasic.VBCodeProvider>O [ \<elemento system.codedom>](system-codedom-element.md) contém configurações de configuração do compilador para provedores de idiomainstalados em um computador, além dos provedores padrão que estão instalados com o .NET Framework, como o e o . Os [ \<compiladores>](compilers-element.md) elemento contém elementos>zero ou mais [ \<compilador.](compiler-element.md) Cada [ \<compilador>](compiler-element.md) elemento especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 Desenvolvedores e fornecedores de compiladores podem adicionar configurações ao arquivo de <xref:System.CodeDom.Compiler.CodeDomProvider> configuração da máquina (Machine.config) para uma nova implementação. Use <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> o método para enumerar de forma programática tanto os provedores de idiomas padrão quanto os provedores de idiomas identificados pelas configurações de configuração do compilador em um computador.  
  
> [!NOTE]
> Nas versões .NET Framework 1.0 e 1.1, os provedores de linguagem padrão fornecidos pelo .NET Framework são identificados no elemento [ \<>compiladores.](compilers-element.md) Na versão 2.0 do .NET Framework, os provedores de linguagem padrão não são identificados <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> nos [ \<compiladores>](compilers-element.md) elemento, mas podem ser enumerados usando o método.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework Versões 1.0 e 1.1  
 O elemento [ \<system.codedom>](system-codedom-element.md) contém as configurações de configuração do compilador para provedores de idiomas em um computador. Os [ \<compiladores>](compilers-element.md) elemento contém elementos>zero ou mais [ \<compilador.](compiler-element.md) Cada [ \<compilador>](compiler-element.md) elemento especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Este elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra uma configuração típica do compilador.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Esquema de arquivo de configuração](../index.md)
- [Esquema de configurações do compilador e do provedor de idiomas](index.md)
- [\<elemento> compilador](compiler-element.md)
