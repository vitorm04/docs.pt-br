---
title: '&lt;compilador&gt; elemento'
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 84000d8762c5d5cfd8d2359a377ffcd5b50ab07c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486747"
---
# <a name="ltcompilergt-element"></a>&lt;compilador&gt; elemento

Especifica os atributos de configuração do compilador para um provedor de linguagem.

\<Elemento de configuração > \<elemento System. CodeDom > \<compiladores de elemento > \<compilador > elemento

## <a name="syntax"></a>Sintaxe

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a>Atributos e elementos

As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|`compilerOptions`|Atributo opcional.<br /><br /> Especifica os argumentos adicionais específicos do compilador para compilação. Os valores para o `compilerOptions` atributo normalmente são listados em um tópico de opções do compilador para o compilador.|
|`extension`|Atributo obrigatório.<br /><br /> Fornece uma lista separada por ponto e vírgula de extensões de nome de arquivo usado por arquivos de origem para o provedor de linguagem. Por exemplo, ".cs".|
|`language`|Atributo obrigatório.<br /><br /> Fornece uma lista separada por vírgulas de nomes de idiomas com suporte pelo provedor de linguagem. Por exemplo, "c#;cs;csharp".|
|`type`|Atributo obrigatório.<br /><br /> Especifica o nome do tipo do provedor de linguagem, incluindo o nome do assembly que contém a implementação do provedor. O nome do tipo deve atender aos requisitos definidos na [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|
|`warningLevel`|Atributo opcional.<br /><br /> Especifica o nível de aviso do compilador padrão; Determina o nível no qual o provedor de linguagem de programação trata avisos de compilação como erros.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|[\<providerOption > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|Especifica atributos de versão do compilador para um provedor de linguagem.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento \<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|
|[\<System. CodeDom > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|Especifica as definições de configuração do compilador para provedores de linguagem disponíveis.|
|[\<compiladores > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|Contêiner para elementos de configuração do compilador; contém zero ou mais `<compiler>` elementos.|

## <a name="remarks"></a>Comentários

Cada `<compiler>` elemento Especifica os atributos de configuração do compilador para um provedor de idioma específico. Estende o provedor do <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> classe para um idioma específico; o `<compiler>` elemento define o compilador e as configurações do gerador de código para o provedor de linguagem de programação.

O .NET Framework define as configurações do compilador iniciais no arquivo de configuração do computador (Machine.config). Os desenvolvedores e fornecedores do compilador podem adicionar parâmetros de configuração em uma nova implementação do <xref:System.CodeDom.Compiler.CodeDomProvider>. Use o método <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> para enumerar programaticamente as definições de configuração do compilador e do provedor de linguagem em um computador.

Elementos de compilador no arquivo de configuração Web ou aplicativo podem suplementar ou substituir as configurações no arquivo de configuração do computador. Se mais de uma implementação de provedor estiver configurada para o mesmo nome do idioma ou a mesma extensão de arquivo, a última configuração correspondente substitui quaisquer provedores anteriores configurados para essa extensão de arquivo ou nome de idioma.

## <a name="configuration-file"></a>Arquivo de Configuração

Esse elemento pode ser usado no arquivo de configuração do computador e o arquivo de configuração do aplicativo.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra um elemento de configuração do compilador típico:

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
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a>Consulte também

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [\<compiladores > elemento](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [Nomes de tipo especificando totalmente qualificados]-(... /.. /.. /.. /.. / docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- [Elemento de compilador para compiladores para compilação (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))
