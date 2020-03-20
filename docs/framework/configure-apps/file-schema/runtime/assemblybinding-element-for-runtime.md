---
title: Elemento <assemblyBinding> para <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding
helpviewer_keywords:
- <assemblyBinding> element
- assemblyBinding element
- container tags, <assemblyBinding> element
ms.assetid: 964cbb35-ab49-4498-8471-209689e5dada
ms.openlocfilehash: 202b063ad3f0f9696cdc12aff434d61fe5a813e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154316"
---
# <a name="assemblybinding-element-for-runtime"></a>\<montagemElemento de \<> de vinculação para> de tempo de execução
Contém informações sobre o redirecionamento de versão e os locais dos assemblies.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<montagem>vinculante**  
  
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
|**xmlns**|Atributo obrigatório.<br /><br /> Especifica o espaço de nome XML necessário para a vinculação do conjunto. Use a string "urna:schemas-microsoft-com:asm.v1" como valor.|  
|**Appliesto**|Especifica a versão em tempo de execução a que o redirecionamento do conjunto .NET Framework se aplica. Este atributo opcional usa um número de versão .NET Framework para indicar a qual versão ele se aplica. Se nenhum atributo **appliesTo** for especificado, o elemento **\<assemblyBinding>** se aplica a todas as versões do .NET Framework. O atributo **appliesTo** foi introduzido na versão 1.1 do .NET Framework; ele é ignorado pela versão .NET Framework 1.0. Isso significa que todos os ** \<elementos de>de montagem Vinculante** são **aplicados** ao usar a versão 1.0 do .NET Framework, mesmo que um atributo applieTo seja especificado.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dependente>de montagem](dependentassembly-element.md)|Encapsula a política de vinculação e o local de montagem para uma montagem. Use ** \<** uma marca de>de montagem dependente para cada montagem.|  
|[\<sondando>](probing-element.md)|Especifica subdiretórios as pesquisas de tempo de execução do idioma comum ao carregar conjuntos.|  
|[\<>de políticas de>](publisherpolicy-element.md)|Especifica se o runtime aplica a política do editor.|  
|[\<qualificar>de montagem](qualifyassembly-element.md)|Especifica o nome completo do assembly que deve ser carregado dinamicamente quando um nome parcial é usado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como redirecionar uma versão de montagem para outra e fornecer uma base de código.  
  
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
  
 O exemplo a seguir mostra como usar o atributo **appliesTo** para redirecionar a vinculação de um conjunto .NET Framework.  
  
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
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Redirecionando versões de assembly](../../redirect-assembly-versions.md)
