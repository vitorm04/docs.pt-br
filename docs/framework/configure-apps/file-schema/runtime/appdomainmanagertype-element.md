---
title: Elemento <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: 8eb6129b3fafaeb81a94d5a4078e41a16583a226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154414"
---
# <a name="appdomainmanagertype-element"></a>\<aplicativoDomainManagerType> Element
Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>de tempo de execução**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<appDomainManagerType>**  
  
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
|`value`|Atributo obrigatório. Especifica o nome do tipo, incluindo o namespace, que serve como o gerenciador de domínio do aplicativo para o domínio de aplicativo padrão no processo.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Para especificar o tipo do gerenciador de domínio do aplicativo, você deve especificar esse elemento e o [ \<aplicativoDomainManagerAssembly>](appdomainmanagerassembly-element.md) elemento. Se um desses elementos não for especificado, o outro será ignorado.  
  
 Quando o domínio de aplicativo <xref:System.TypeLoadException> padrão é carregado, é jogado se o tipo especificado não existir no conjunto especificado pelo [ \<elemento appDomainManagerAssembly>;](appdomainmanagerassembly-element.md) e o processo não começa.  
  
 Quando você especifica o tipo de gerenciador de domínio de aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio do aplicativo padrão herdam o tipo de gerenciador de domínio do aplicativo. Use <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> as <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> propriedades e as propriedades para especificar um tipo diferente de gerenciador de domínio de aplicativo para um novo domínio de aplicativo.  
  
 Especificar o tipo de gerenciador de domínio do aplicativo requer que o aplicativo tenha total confiança. (Por exemplo, um aplicativo em execução na área de trabalho tem total confiança.) Se o aplicativo não tiver <xref:System.TypeLoadException> total confiança, um é jogado.  
  
 O formato do tipo e namespace é o <xref:System.Type.FullName%2A?displayProperty=nameWithType> mesmo formato que é usado para a propriedade.  
  
 Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o gerenciador `MyMgr` de domínio `AdMgrExample` do aplicativo para o domínio de aplicativo padrão de um processo é o tipo no conjunto.  
  
```xml  
<configuration>  
   <runtime>  
      <appDomainManagerType value="MyMgr" />  
      <appDomainManagerAssembly
         value="AdMgrExample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=6856bccf150f00b3" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType>
- <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType>
- [\<appDomainManagerO> Elemento](appdomainmanagerassembly-element.md)
- [Esquema de configurações do runtime](index.md)
- [Esquema de arquivo de configuração](../index.md)
- [Método SetAppDomainManagerType](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
