---
title: Elemento <providerOption>
ms.date: 03/30/2017
f1_keywords:
- provideroption
helpviewer_keywords:
- <provideroption> element
- providerOptions
- provideroption element
ms.assetid: 014f2e0b-c0b5-4fc4-92d3-73f02978b2a1
ms.openlocfilehash: c8ba5b9a0680f5e5102c13eb5bb0c1904a168c07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155395"
---
# <a name="provideroption-element"></a>\<providerOpção> Elemento
Especifica os atributos da versão do compilador para um provedor de idiomas.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.codedom>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<compiladores>**](compilers-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>do compilador**](compiler-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<provedorOpção>**

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
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome da opção; por exemplo, "CompilerVersion".|  
|`value`|Atributo obrigatório.<br /><br /> Especifica o valor da opção; por exemplo, "v3.5".|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<elemento> de configuração](../configuration-element.md)|O elemento raiz em todos os arquivos de configuração que é usado pelo common language runtime e aplicativos do .NET Framework.|  
|[\<system.codedom> Element](system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|  
|[\<compiladores> Element](compilers-element.md)|Recipiente para elementos de configuração do compilador; contém zero `<compiler>` ou mais elementos.|  
|[\<elemento> compilador](compiler-element.md)|Especifica os atributos de configuração do compilador para um provedor de linguagem.|  
  
## <a name="remarks"></a>Comentários  
 Na versão 3.5 do .NET Framework, os provedores de código Code Document Object `<providerOption>` Model (CodeDOM) podem suportar opções específicas do provedor usando o elemento.  
  
 O .NET Framework 3.5 inclui conjuntos atualizados do .NET Framework 2.0 e fornece novas montagens de versão 3.5 que contêm novos tipos. Os provedores de código Microsoft C# e Visual Basic estão contidos em conjuntos .NET Framework 2.0, mas foram atualizados para suportar compiladores da versão 3.5. Por padrão, os provedores de código atualizados geram código para compiladores da versão 2.0. Você pode `<providerOption>` usar o elemento para alterar a versão do compilador de destino para 3.5. Para fazer isso, especifique "CompilerVersion" para o `name` `value` atributo e "v3.5" para o atributo. Você deve preceder o número da versão com um "v" minúsculo.  
  
 Você pode tornar a especificação `<providerOption>` da versão global adicionando o elemento ao arquivo .NET Framework 2.0 Machine.config ou root Web.config. Se você atualizar a versão do compilador padrão para 3.5 no arquivo Machine.config, você poderá alterá-la de volta para 2.0 por aplicativo usando o `<providerOption>` elemento no arquivo de configuração do aplicativo.  
  
 Os implementadores do provedor de código CodeDOM podem `providerOptions` processar opções personalizadas fornecendo um construtor que leva um parâmetro do tipo <xref:System.Collections.Generic.IDictionary%602>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra como especificar que a versão 3.5 do provedor de código C# deve ser usada.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Esquema de arquivo de configuração](../index.md)
- [\<compiladores> Element](compilers-element.md)
- [Especificando nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [elemento compilador para compiladores para compilação (ASP.NET Configurações Esquema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a15ebt6c(v=vs.100))
