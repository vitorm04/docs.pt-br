---
title: "/appconfig (Opções do Compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /appconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: ced4927526d86d29c502a898c60c528df497bb56
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="appconfig-c-compiler-options"></a>/appconfig (opções do compilador C#)
A opção do compilador **/appconfig** habilita um aplicativo em C# a especificar o local de um arquivo de configuração de aplicativo (app.config) de um assembly para o Common Language Runtime (CLR) no tempo de associação do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Necessário. O arquivo de configuração de aplicativo que contém as configurações de associação de assembly.  
  
## <a name="remarks"></a>Comentários  
 O **/appconfig** pode ser usado em cenários avançados, nos quais é necessário que um assembly referencie simultaneamente a versão do .NET Framework e a versão do .NET Framework para o Silverlight de um assembly de referência específico. Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) pode ter que referenciar a Área de Trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF incluído no Silverlight. O mesmo assembly do designer deve acessar ambos os assemblies. Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.  
  
 A opção do compilador **/appconfig** habilita a especificação do local de um arquivo app.config que desabilita o comportamento padrão por meio de uma marca `<supportPortability>`, conforme mostrado no exemplo a seguir.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 O compilador passa o local do arquivo para a lógica de associação de assembly do CLR.  
  
> [!NOTE]
>  Caso o Microsoft Build Engine (MSBuild) seja usado para compilar o aplicativo, é possível definir a opção do compilador **/appconfig** adicionando uma marca de propriedade ao arquivo .csproj. Para usar o arquivo app.config que já está definido no projeto, adicione a marca de propriedade `<UseAppConfigForCompiler>` ao arquivo .csproj e defina seu valor para `true`. Para especificar um arquivo app.config diferente, adicione a marca de propriedade `<AppConfigForCompiler>` e defina seu valor para o local do arquivo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um arquivo app.config que habilita um aplicativo a referenciar as implementações do .NET Framework e do .NET Framework para Silverlight de qualquer assembly do .NET Framework que exista em ambas as implementações. A opção do compilador **/appconfig** especifica o local desse arquivo app.config.  
  
```xml  
<configuration>  
      <runtime>  
      <assemblyBinding>  
            <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
            <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
      </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Visão Geral da Unificação de Assemblies no .NET Framework](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)   
 [\<supportPortability> Element](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)   
 [Opções do compilador de C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
