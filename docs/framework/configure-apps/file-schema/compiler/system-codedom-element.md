---
title: '&lt;System. CodeDom&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.codedom
helpviewer_keywords:
- compiler configuration elements, <system.codedom> element
- system.codedom element
- <system.codedom> element
ms.assetid: 672a68f7-e69f-4479-ac30-e980085ec4fe
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ea9fd06887c9a4bc9f121945f27753dfc666cfec
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078379"
---
# <a name="ltsystemcodedomgt-element"></a>&lt;System. CodeDom&gt; elemento
Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.  
  
 \<Configuração > elemento  
\<System. CodeDom > elemento  
  
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
|[\<compilers>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="net-framework-version-20"></a>.NET framework versão 2.0  
 O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém definições de configuração do compilador para provedores de linguagem instalados em um computador, além de provedores padrão que são instalados com o .NET Framework, como o <xref:Microsoft.CSharp.CSharpCodeProvider> e o <xref:Microsoft.VisualBasic.VBCodeProvider>. O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos. Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 Os desenvolvedores e fornecedores do compilador podem adicionar definições de configuração para o arquivo de configuração de máquina (Machine. config) para um novo <xref:System.CodeDom.Compiler.CodeDomProvider> implementação. Use o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> método para enumerar programaticamente os provedores de linguagem padrão e de provedores de linguagem identificados pelos parâmetros de configuração do compilador em um computador.  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o idioma padrão provedores fornecidos pelo .NET Framework são identificados na [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento. O .NET Framework versão 2.0, os provedores de linguagem padrão não são identificados na [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento, mas podem ser enumerados usando o <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A> método.  
  
## <a name="net-framework-versions-10-and-11"></a>Versões 1.0 e 1.1 do .NET framework  
 O [ \<System. CodeDom >](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md) elemento contém as definições de configuração do compilador para provedores de linguagem em um computador. O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém zero ou mais [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elementos. Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração do computador e o arquivo de configuração do aplicativo.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Esquema de configurações de compilador e de provedor de idiomas](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
