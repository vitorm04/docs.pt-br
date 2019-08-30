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
ms.openlocfilehash: 19f37095bd01b76fda8b1e29423c413dbdb06a65
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168911"
---
# <a name="systemcodedom-element"></a>\<Elemento de > System. CodeDom
Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp;&nbsp; **\<> System. CodeDom**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.codedom>  
  <compilers> ... </compilers>  
</system.codedom>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<compilers>](compilers-element.md)|Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](compiler-element.md).|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="net-framework-version-20"></a>.NET Framework versão 2,0  
 <xref:Microsoft.CSharp.CSharpCodeProvider> O [ \<elemento System. CodeDom >](system-codedom-element.md) contém definições de configuração de compilador para provedores de idiomas instalados em um computador além dos provedores padrão instalados com o .NET Framework, como o e o <xref:Microsoft.VisualBasic.VBCodeProvider>. O elemento [ \<>](compilers-element.md) de compiladores contém zero ou mais [ \<](compiler-element.md) elementos de > do compilador. Cada elemento > do compilador Especifica os atributos de configuração do compilador para um provedor de idioma específico. [ \<](compiler-element.md)  
  
 Os desenvolvedores e fornecedores de compilador podem adicionar definições de configuração ao arquivo de configuração da máquina (Machine. config <xref:System.CodeDom.Compiler.CodeDomProvider> ) para uma nova implementação. Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente os provedores de idioma padrão e os provedores de idiomas identificados pelas definições de configuração do compilador em um computador.  
  
> [!NOTE]
> No .NET Framework versões 1,0 e 1,1, os provedores de idioma padrão fornecidos pelo .NET Framework são identificados no [ \<elemento compiladores >](compilers-element.md) . No .NET Framework versão 2,0, os provedores de idioma padrão não são identificados no <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> [ \<elemento compiladores >](compilers-element.md) , mas podem ser enumerados usando o método.  
  
## <a name="net-framework-versions-10-and-11"></a>.NET Framework versões 1,0 e 1,1  
 O elemento System [. CodeDom > contém as definições de configuração do compilador para os provedores de idioma em um computador. \<](system-codedom-element.md) O elemento [ \<>](compilers-element.md) de compiladores contém zero ou mais [ \<](compiler-element.md) elementos de > do compilador. Cada elemento > do compilador Especifica os atributos de configuração do compilador para um provedor de idioma específico. [ \<](compiler-element.md)  
  
 O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir ilustra uma configuração de compilador típica.  
  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Esquema de arquivos de configuração](../index.md)
- [Esquema de configurações de compilador e de provedor de idiomas](index.md)
- [\<compiler> Element](compiler-element.md)
