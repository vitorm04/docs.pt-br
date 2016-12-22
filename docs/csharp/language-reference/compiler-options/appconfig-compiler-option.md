---
title: "/appconfig (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/appconfig"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/appconfig compiler option [C#]"
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /appconfig (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A opção do compilador de **\/appconfig** permite que um aplicativo C\# para especificar o local do arquivo de configuração do aplicativo de um assembly app.config\) a \(Common Language Runtime \(CLR\) no momento da associação do assembly.  
  
## Sintaxe  
  
```  
/appconfig:file  
```  
  
## Arguments  
 `file`  
 Obrigatório.  O arquivo de configuração do aplicativo que contém as configurações de associação do assembly.  
  
## Comentários  
 Um uso de **\/appconfig** é cenários avançados em que um assembly precisa fazer referência à versão do .NET Framework e o .NET Framework para a versão do Silverlight de um assembly específico de referência ao mesmo tempo.  Por exemplo, um designer XAML gravado no Windows Presentation Foundation \(WPF\) pode ter que fazer referência WPF Área De Trabalho, para a interface de usuário do designer, e o subconjunto de WPF que é incluído com o Silverlight.  O mesmo assembly do designer precisa acessar os assemblies.  Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly enxerga os dois assemblies como equivalentes.  
  
 A opção do compilador de **\/appconfig** permite especificar o local de um arquivo app.config que desabilita o comportamento padrão usando uma marca de `<supportPortability>` , conforme mostrado no exemplo a seguir.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 O compilador passa o local do arquivo à lógica de assembly a associação de CLR.  
  
> [!NOTE]
>  Se você estiver usando o Mecanismo de compilação \(Microsoft MSBuild\) para criar seu aplicativo, você pode definir a opção do compilador de **\/appconfig** adicionando uma marca de propriedade no arquivo de .csproj.  Para usar o arquivo app.config que já está definido no projeto, adicione a marca `<UseAppConfigForCompiler>` da propriedade no arquivo de .csproj e defina seu valor como `true`.  Para especificar um arquivo app.config diferente, adicione a marca `<AppConfigForCompiler>` de propriedade e defina seu valor com o local do arquivo.  
  
## Exemplo  
 O exemplo a seguir mostra um arquivo app.config que permite que um aplicativo ter referências à implementação do.NET Framework e o .NET Framework para a implementação do Silverlight de qualquer assembly do .NET Framework existentes em ambas as implementações.  A opção do compilador de **\/appconfig** especifica o local deste arquivo app.config.  
  
```  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## Consulte também  
 [.NET Framework Assembly Unification Overview](http://msdn.microsoft.com/pt-br/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)   
 [Elemento \<supportPortability\>](../Topic/%3CsupportPortability%3E%20Element.md)   
 [C\# Compiler Options Listed Alphabetically](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)