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
ms.openlocfilehash: b09c2a1f67974a67a3f9d58af7cb8cf66a197026
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088697"
---
# <a name="compilers-element"></a>\<compiladores > elemento
Contêiner de elementos de configuração do compilador. Contém zero ou mais elementos [\<compiler>](compiler-element.md).  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. codedom >** ](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**compiladores\<**

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
|[\<compiler> Element](compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|[\<elemento > System. CodeDom](system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
  
## <a name="remarks"></a>Comentários  
 O elemento [> de compiladores do\<](compilers-element.md) contém as definições de configuração do compilador para provedores de idiomas em um computador. Cada [\<do compilador >](compiler-element.md) especifica os atributos de configuração do compilador para um provedor de idioma específico.  
  
 O .NET Framework define as configurações iniciais do compilador e do provedor de idiomas no arquivo de configuração da máquina (Machine. config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina e no arquivo de configuração do aplicativo.  
  
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
- [Esquema de configurações de compilador e de provedor de idiomas](index.md)
- [\<compiler> Element](compiler-element.md)
