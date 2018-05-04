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
manager: markl
ms.openlocfilehash: fc85610f5c3db7929f824fda2dd211300d9b05c1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcompilersgt-element"></a>&lt;compiladores&gt; elemento
Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md).  
  
 \<configuration>  
\<System. CodeDom >  
\<compiladores > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|[\<System. CodeDom > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
  
## <a name="remarks"></a>Comentários  
 O [ \<compiladores >](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md) elemento contém as definições de configuração do compilador para provedores de linguagem em um computador. Cada [ \<compilador >](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md) elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 O .NET Framework define o compilador inicial e configurações de idioma do provedor no arquivo de configuração da máquina (Machine. config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração de máquina e o arquivo de configuração do aplicativo.  
  
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
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Esquema de configurações de compilador e de provedor de idiomas](../../../../../docs/framework/configure-apps/file-schema/compiler/index.md)  
 [\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)
