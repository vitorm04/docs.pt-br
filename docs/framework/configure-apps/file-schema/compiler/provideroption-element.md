---
title: '&lt;providerOption&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 75cc2003a88cc7be467b9062c37b6b5d9eb82f53
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337870"
---
# <a name="ltprovideroptiongt-element"></a>&lt;providerOption&gt; elemento
Especifica os atributos de versão do compilador para um provedor de linguagem.  
  
 \<Elemento de configuração >  
\<Elemento System. CodeDom >  
\<compiladores de elemento >  
\<compilador > elemento  
\<providerOption > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<providerOption  
  name="option-name"  
  value="option-value"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome da opção. Por exemplo, "CompilerVersion".|  
|`value`|Atributo obrigatório.<br /><br /> Especifica o valor para a opção. Por exemplo, "v3.5".|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.|  
|[\<System. CodeDom > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
|[\<compiladores > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Contêiner para elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 3.5, provedores de código de Code Document Object Model (CodeDOM) podem dar suporte a opções específicas do provedor usando o `<providerOption>` elemento.  
  
 O .NET Framework 3.5 inclui assemblies do .NET Framework 2.0 atualizados e fornece novos assemblies da versão 3.5 que contêm os novos tipos. Os provedores de código Microsoft c# e Visual Basic estão contidos em assemblies do .NET Framework 2.0, mas foram atualizados para dar suporte a compiladores versão 3.5. Por padrão, os provedores de código atualizado geram código para compiladores versão 2.0. Você pode usar o `<providerOption>` elemento para alterar a versão do compilador de destino para 3.5. Para fazer isso, especifique "CompilerVersion" para o `name` atributo e "v3.5" para o `value` atributo. Você deve preceder o número de versão com um "v" em letras minúsculas.  
  
 Você pode tornar a especificação de versão global adicionando o `<providerOption>` elemento para o Machine. config do .NET Framework 2.0 ou o arquivo Web. config de raiz. Se você atualizar a versão do compilador padrão para 3.5 no arquivo Machine. config, você pode alterá-lo para 2.0 em uma base por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.  
  
 Implementadores de provedor de código codeDOM podem processar opções personalizadas, fornecendo um construtor que usa um `providerOptions` parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como especificar a versão 3.5 do provedor de código c# deve ser usado.  
  
```xml  
<configuration>  
  <system.codedom>  
    <compilers>  
      <!-- zero or more compiler elements -->  
      <compiler  
        language="c#;cs;csharp"  
        extension=".cs"  
        type="Microsoft.CSharp.CSharpCodeProvider, System,   
          Version=2.0.3600.0, Culture=neutral,   
          PublicKeyToken=b77a5c561934e089"  
        compilerOptions="/optimize"  
        warningLevel="1" >  
          <providerOption  
            name="CompilerVersion"  
            value="v3.5" />  
      </compiler>  
    </compilers>  
  </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.CodeDom.Compiler.CompilerInfo>  
 <xref:System.CodeDom.Compiler.CodeDomProvider>  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<compiladores > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)  
 [Especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)  
 [Elemento de compilador para compiladores para compilação (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
