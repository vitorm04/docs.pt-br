---
title: "&lt;Opção&gt; elemento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
caps.latest.revision: "22"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1f91b9fcd7ef9c9c616a7a41ced6be1cda365509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltprovideroptiongt-element"></a>&lt;Opção&gt; elemento
Especifica os atributos de versão do compilador para um provedor de idioma.  
  
 \<Elemento de configuração >  
\<Elemento System. CodeDom >  
\<compiladores de elemento >  
\<compilador > elemento  
\<Opção > elemento  
  
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
|`value`|Atributo obrigatório.<br /><br /> Especifica o valor para a opção. Por exemplo, "v. 3.5".|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.|  
|[\<System. CodeDom > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
|[\<compiladores > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Contêiner de elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.|  
|[\<compiler> Element](../../../../../docs/framework/configure-apps/file-schema/compiler/compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
## <a name="remarks"></a>Comentários  
 No .NET Framework versão 3.5, provedores de código de modelo de objeto de documento de código (CodeDOM) podem dar suporte a opções específicas do provedor usando o `<providerOption>` elemento.  
  
 O .NET Framework 3.5 inclui assemblies do .NET Framework 2.0 atualizados e fornece novos assemblies da versão 3.5 que contêm os novos tipos. Os provedores de código Microsoft c# e Visual Basic estão contidos em assemblies do .NET Framework 2.0, mas foram atualizados para dar suporte a compiladores versão 3.5. Por padrão, os provedores de código atualizado geram código para compiladores versão 2.0. Você pode usar o `<providerOption>` elemento para alterar a versão do compilador destino 3.5. Para fazer isso, especifique "CompilerVersion" para o `name` atributo e "v 3.5" para o `value` atributo. Você deve preceder o número de versão com "v" em letras minúsculas.  
  
 Você pode fazer a especificação de versão global adicionando o `<providerOption>` elemento o Machine. config do .NET Framework 2.0 ou o arquivo Web. config de raiz. Se você atualizar a versão do compilador padrão 3.5 no arquivo Machine. config, você pode alterá-la para 2.0 em uma base por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.  
  
 Implementadores de provedor codeDOM código podem processar opções personalizadas, fornecendo um construtor que aceita um `providerOptions` parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como especificar que a versão 3.5 do provedor de código c# deve ser usada.  
  
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
 [compilador elemento compiladores para compilação (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/f7d6b078-5d42-4134-b3f7-62e1aba1df1e)
