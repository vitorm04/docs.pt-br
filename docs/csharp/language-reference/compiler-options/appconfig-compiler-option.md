---
title: -appconfig (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
ms.openlocfilehash: 33f79967c34736f2175e0bb6e2b5b88d211545c2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398502"
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (opções do compilador C#)
A opção do compilador **-appconfig** permite que um aplicativo em C# especifique o local de um arquivo de configuração de aplicativo (app.config) de um assembly para o CLR (Common Language Runtime) em tempo de associação do assembly.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 Necessário. O arquivo de configuração de aplicativo que contém as configurações de associação de assembly.  
  
## <a name="remarks"></a>Comentários  
 O **-appconfig** pode ser usado em cenários avançados, nos quais é necessário que um assembly referencie, ao mesmo temo, tanto a versão do .NET Framework quanto a versão do .NET Framework para a versão do Silverlight de um assembly de referência específico. Por exemplo, um designer XAML gravado no Windows Presentation Foundation (WPF) pode ter que referenciar a Área de Trabalho do WPF, para a interface do usuário do designer e o subconjunto do WPF incluído no Silverlight. O mesmo assembly do designer deve acessar ambos os assemblies. Por padrão, as referências separadas causam um erro do compilador, pois a associação de assembly considera os dois assemblies equivalentes.  
  
 A opção do compilador **-appconfig** permite a especificação do local de um arquivo app.config que desabilita o comportamento padrão por meio de uma marcação `<supportPortability>`, conforme mostrado no exemplo a seguir.  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 O compilador passa o local do arquivo para a lógica de associação de assembly do CLR.  
  
> [!NOTE]
>  Caso o MSBuild (Microsoft Build Engine) seja usado para compilar o aplicativo, é possível definir a opção do compilador **-appconfig** adicionando uma marcação de propriedade ao arquivo .csproj. Para usar o arquivo app.config que já está definido no projeto, adicione a marca de propriedade `<UseAppConfigForCompiler>` ao arquivo .csproj e defina seu valor para `true`. Para especificar um arquivo app.config diferente, adicione a marca de propriedade `<AppConfigForCompiler>` e defina seu valor para o local do arquivo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra um arquivo app.config que habilita um aplicativo a referenciar as implementações do .NET Framework e do .NET Framework para Silverlight de qualquer assembly do .NET Framework que exista em ambas as implementações. A opção do compilador **-appconfig** especifica o local desse arquivo app.config.  
  
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

- [Elemento \<supportPortability>](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
- [Opções do compilador de C# listadas em ordem alfabética](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
