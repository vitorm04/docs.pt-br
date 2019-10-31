---
title: Elemento <appDomainManagerType>
ms.date: 03/30/2017
helpviewer_keywords:
- appDomainManagerType element
- <appDomainManagerType> element
ms.assetid: ae8d5a7e-e7f7-47f7-98d9-455cc243a322
ms.openlocfilehash: bae4aa39f9c43480ac2ef984f78834b68646742d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118236"
---
# <a name="appdomainmanagertype-element"></a>\<elemento de > appDomainManagerType
Especifica o tipo que serve como o gerenciador de domínio do aplicativo para o domínio do aplicativo padrão.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<appDomainManagerType >**  
  
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
 Para especificar o tipo de Gerenciador de domínio do aplicativo, você deve especificar esse elemento e o elemento [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) . Se um desses elementos não for especificado, o outro será ignorado.  
  
 Quando o domínio de aplicativo padrão for carregado, <xref:System.TypeLoadException> será gerada se o tipo especificado não existir no assembly especificado pelo elemento [\<appDomainManagerAssembly >](appdomainmanagerassembly-element.md) ; e o processo não é iniciado.  
  
 Quando você especifica o tipo de Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão, outros domínios de aplicativo criados a partir do domínio de aplicativo padrão herdam o tipo de Gerenciador de domínio do aplicativo. Use as propriedades <xref:System.AppDomainSetup.AppDomainManagerType%2A?displayProperty=nameWithType> e <xref:System.AppDomainSetup.AppDomainManagerAssembly%2A?displayProperty=nameWithType> para especificar um tipo de Gerenciador de domínio de aplicativo diferente para um novo domínio de aplicativo.  
  
 A especificação do tipo de Gerenciador de domínio do aplicativo exige que o aplicativo tenha confiança total. (Por exemplo, um aplicativo em execução na área de trabalho tem confiança total.) Se o aplicativo não tiver confiança total, um <xref:System.TypeLoadException> será gerado.  
  
 O formato do tipo e do namespace é o mesmo formato usado para a propriedade <xref:System.Type.FullName%2A?displayProperty=nameWithType>.  
  
 Este elemento de configuração está disponível apenas no .NET Framework 4 e posterior.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como especificar que o Gerenciador de domínio do aplicativo para o domínio de aplicativo padrão de um processo é o tipo de `MyMgr` no assembly `AdMgrExample`.  
  
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
- [\<elemento de > appDomainManagerAssembly](appdomainmanagerassembly-element.md)
- [Esquema de configurações do tempo de execução](index.md)
- [Esquema de arquivos de configuração](../index.md)
- [Método SetAppDomainManagerType](../../../unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)
