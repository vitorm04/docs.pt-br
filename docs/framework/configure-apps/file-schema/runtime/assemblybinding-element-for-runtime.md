---
title: '&lt;assemblyBinding&gt; elemento para &lt;tempo de execução&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33900f40aab85fd67540ecd6004a46e13e8eb8c2
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612030"
---
# <a name="ltassemblybindinggt-element-for-ltruntimegt"></a>&lt;assemblyBinding&gt; elemento para &lt;tempo de execução&gt;
Contém informações sobre o redirecionamento de versão e os locais dos assemblies.  
  
 \<configuration>  
\<runtime>  
\<assemblyBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <assemblyBinding    
   xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
</assemblyBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**xmlns**|Atributo obrigatório.<br /><br /> Especifica o namespace XML necessário para a associação de assembly. Use a cadeia de caracteres "urn: schemas-microsoft-v1" como o valor.|  
|**Aplica-se**|Especifica a versão de tempo de execução, a que o redirecionamento de assembly do .NET Framework se aplica. Esse atributo opcional usa um número de versão do .NET Framework para indicar qual versão ele se aplica ao. Se nenhum atributo **appliesTo** for especificado, o elemento **\<assemblyBinding>** se aplica a todas as versões do .NET Framework. O **appliesTo** atributo foi introduzido no .NET Framework versão 1.1; ele será ignorado pelo .NET Framework versão 1.0. Isso significa que todos os elementos **\<assemblyBinding>** são aplicados ao usar o .NET Framework versão 1.0, mesmo se um atributo **appliesTo** for especificado.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dependentAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Encapsula o local de assembly e política de associação para um assembly. Use um  **\<dependentAssembly >** marca para cada assembly.|  
|[\<probing>](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Especifica os subdiretórios que o common language runtime procura ao carregar assemblies.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Especifica se o tempo de execução aplica a política do editor.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como redirecionar uma versão do assembly para outra e fornecer uma base de código.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
            <codeBase version="2.0.0.0"  
                      href="http://www.litwareinc.com/myAssembly.dll"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 O exemplo a seguir mostra como usar o **appliesTo** atributo para redirecionar a associação de um assembly do .NET Framework.  
  
```xml  
<runtime>  
   <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1" appliesTo="v1.0.3705">  
      <dependentAssembly>   
         <assemblyIdentity name="mscorcfg" publicKeyToken="b03f5f7f11d50a3a" culture=""/>  
         <bindingRedirect oldVersion="0.0.0.0-65535.65535.65535.65535" newVersion="1.0.3300.0"/>  
      </dependentAssembly>  
   </assemblyBinding>  
</runtime>  
```  
  
## <a name="see-also"></a>Consulte também  
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [Redirecionando versões de assembly](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
