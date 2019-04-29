---
title: Elemento <appDomainManagerAssembly>
ms.date: 03/30/2017
helpviewer_keywords:
- <appDomainManagerAssembly> element
- appDomainManagerAssembly element
ms.assetid: c7c56e39-a700-44f5-b94e-411bfce339d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fe1dfbd62a6967ae51031fa12f80e9c5563dc44
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704915"
---
# <a name="appdomainmanagerassembly-element"></a>\<appDomainManagerAssembly > elemento
Especifica o assembly que fornece o gerenciador do domínio do aplicativo para o domínio do aplicativo padrão no processo.  
  
 \<configuration>  
\<runtime>  
\<appDomainManagerAssembly>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<appDomainManagerAssembly   
   value="assembly display name" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`value`|Atributo obrigatório. Especifica o nome de exibição do assembly que fornece o Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão no processo.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Para especificar o tipo de Gerenciador de domínio, você deve especificar ambos os esse elemento e o [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elemento. Se qualquer um desses elementos não for especificado, o outro será ignorado.  
  
 Quando o domínio de aplicativo padrão é carregado, <xref:System.TypeLoadException> é lançada se o assembly especificado não existe ou se o assembly não contém o tipo especificado pelo [ \<appDomainManagerType >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md) elemento; e o processo falha ao iniciar. Se o assembly for encontrado, mas não coincide com as informações de versão, um <xref:System.IO.FileLoadException> é gerada.  
  
 Quando você especifica o tipo de Gerenciador de domínio de aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo. Use o <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> e <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriedades para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.  
  
 Especificar o tipo de Gerenciador de domínio de aplicativo requer que o aplicativo tenha confiança total. (Por exemplo, um aplicativo em execução na área de trabalho tem confiança total). Se o aplicativo não tem confiança total, um <xref:System.TypeLoadException> é gerada.  
  
 Para o formato do nome de exibição do assembly, consulte o <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> propriedade.  
  
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
- [\<appDomainManagerType > elemento](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Método SetAppDomainManagerType](../../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
