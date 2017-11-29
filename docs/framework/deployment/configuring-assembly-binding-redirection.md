---
title: "Configurando o redirecionamento de associações de assemblies"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: d266cbd8-bf91-41d1-baf0-afbc481a741f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ff3f56b08aa3d6c7cb05bafd98d26f4700fa4e5a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-assembly-binding-redirection"></a>Configurando o redirecionamento de associações de assemblies
Por padrão, os aplicativos usam o conjunto de assemblies do .NET Framework que acompanha a versão do tempo de execução usada para compilar o aplicativo. Você pode usar o atributo **appliesTo** no elemento [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) em um arquivo de configuração de aplicativo para redirecionar referências de associação de assembly para uma versão específica de assemblies do .NET Framework. Esse atributo opcional usa um número de versão do .NET Framework para indicar a qual versão ele se aplica. Se nenhum atributo **appliesTo** for especificado, o elemento **\<assemblyBinding>** se aplica a todas as versões do .NET Framework.  
  
 O atributo **appliesTo** foi introduzido no.NET Framework versão 1.1; ele é ignorado pelo .NET Framework versão 1.0. Isso significa que todos os elementos **\<assemblyBinding>** são aplicados ao usar o .NET Framework versão 1.0, mesmo se um atributo **appliesTo** for especificado.  
  
> [!NOTE]
>  Use o atributo **appliesTo** para limitar o redirecionamento de associação de assembly para uma versão específica do tempo de execução.  
  
 Por exemplo, para redirecionar a associação de assembly para um assembly do .NET Framework versão 1.0, inclua código XML a seguir no seu arquivo de configuração de aplicativo.  
  
```xml  
<runtime>  
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
            <dependentAssembly>   
               * assembly information goes here *  
            </dependentAssembly>  
       </assemblyBinding>  
</runtime>  
```  
  
 Os elementos **\<assemblyBinding>** fazem distinção conforme a ordem. Insira as informações de redirecionamento de associação de assembly primeiramente para os assemblies do .NET Framework versão 1.0, seguido pelas informações de redirecionamento de associação de assembly para os assemblies do .NET Framework versão 1.1. Por fim, insira as informações de redirecionamento de associação de assembly para qualquer redirecionamento de assembly do .NET Framework que não use o atributo **appliesTo** e, portanto, se aplica a todas as versões do .NET Framework. No caso de um conflito de redirecionamento, a primeira instrução de redirecionamento correspondente no arquivo de configuração é usada.  
  
 Por exemplo, para redirecionar uma referência a um assembly do .NET Framework versão 1.0 e outra referência a um assembly do .NET Framework versão 1.1, use o padrão mostrado no pseudocódigo a seguir.  
  
```xml  
<assemblyBinding xmlns="..." appliesTo="v1.0.3705">   
<! — .NET Framework version 1.0 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="..." appliesTo="v1.1.4322">   
    <! — .NET Framework version 1.1 redirects here. -->   
</assemblyBinding>   
  
<assemblyBinding xmlns="...">   
<!-- Redirects meant for all versions of the .NET Framework. -->   
</assemblyBinding>  
```  
  
## <a name="debugging-configuration-file-errors"></a>Depurando erros de arquivos de configuração  
 O tempo de execução analisa os arquivos de configuração uma vez quando um domínio do aplicativo é criado e carrega o código para ele. O Common Language Runtime trata os erros em um arquivo de configuração ignorando a entrada. O tempo de execução ignorará todo o arquivo de configuração se ele contiver XML mal formado. Para XML inválido, apenas as seções inválidas serão ignoradas.  
  
 É possível identificar se um arquivo de configuração está sendo usado determinando se os redirecionamentos de associação de assembly estão ocorrendo. Use o [Visualizador de Log de Associação de Assembly (Fuslogvw.exe)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) para ver quais assemblies são carregados. Para ver todas as associações de assembly, você deve definir uma entrada para **ForceLog** no registro.  
  
## <a name="see-also"></a>Consulte também  
 [Como habilitar e desabilitar o redirecionamento automático de associações](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
