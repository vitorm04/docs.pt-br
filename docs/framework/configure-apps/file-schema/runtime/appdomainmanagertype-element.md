---
title: <appDomainManagerType> Elemento
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7aa13d26ac11ed624caa4c9704325f2d604418bd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164210"
---
# <a name="appdomainmanagertype-element"></a>\<appDomainManagerType > elemento
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
|`value`|Atributo obrigatório. Especifica o nome do tipo, incluindo o namespace, que serve como o Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão no processo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Para especificar o tipo de Gerenciador de domínio, você deve especificar ambos os esse elemento e o [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elemento. Se qualquer um desses elementos não for especificado, o outro será ignorado.  
  
 Quando o domínio de aplicativo padrão é carregado, <xref:System.TypeLoadException> será lançada se o tipo especificado não existe no assembly especificado pela [ \<appDomainManagerAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md) elemento; e o processo de falha para Inicie.  
  
 Quando você especifica o tipo de Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo. Use o <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> e <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriedades para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.  
  
 Especificar o tipo de Gerenciador de domínio de aplicativo requer que o aplicativo tenha confiança total. (Por exemplo, um aplicativo em execução na área de trabalho tem confiança total). Se o aplicativo não tem confiança total, um <xref:System.TypeLoadException> é gerada.  
  
 O formato do tipo e namespace é o mesmo formato que é usado para o <xref:System.Type.FullName%2A?displayProperty=nameWithType> propriedade.  
  
 Este elemento de configuração está disponível apenas no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] e versões posteriores.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão de um processo é o `MyMgr` digite o `AdMgrExample` assembly.  
  
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
- [\<appDomainManagerAssembly > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Método SetAppDomainManagerType](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
