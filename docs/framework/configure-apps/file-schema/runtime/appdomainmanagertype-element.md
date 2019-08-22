---
title: Elemento <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b535ba67ab05dabd7e0a23e79692bbf69e25b55
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663918"
---
# <a name="appdomainmanagertype-element"></a>\<Elemento de > appDomainManagerType
Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.  
  
 \<configuration>  
\<runtime>  
\<appDomainManagerType>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<appDomainManagerAssembly   
   value="type name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`value`|Atributo obrigatório. Especifica o nome do tipo, incluindo o namespace, que serve como o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Para especificar o tipo de Gerenciador de domínio do aplicativo, você deve especificar esse elemento e o elemento de [ \<> appDomainManagerAssembly](appdomainmanagerassembly-element.md) . Se um desses elementos não for especificado, o outro será ignorado.  
  
 Quando o domínio de aplicativo padrão for carregado <xref:System.TypeLoadException> , será gerado se o tipo especificado não existir no assembly especificado pelo elemento de [ \<> appDomainManagerAssembly](appdomainmanagerassembly-element.md) ; e o processo não for iniciado.  
  
 Quando você especifica o tipo de Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo. Use as <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> propriedades <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> e para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.  
  
 A especificação do tipo de Gerenciador de domínio do aplicativo exige que o aplicativo tenha confiança total. (Por exemplo, um aplicativo em execução na área de trabalho tem confiança total.) Se o aplicativo não tiver confiança total, um <xref:System.TypeLoadException> será lançado.  
  
 O formato do tipo e do namespace é o mesmo formato usado para a <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade.  
  
 Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão de um `MyMgr` processo é o `AdMgrExample` tipo no assembly.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly   
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<Elemento de > appDomainManagerAssembly](appdomainmanagerassembly-element.md)
- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Método SetAppDomainManagerType](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
