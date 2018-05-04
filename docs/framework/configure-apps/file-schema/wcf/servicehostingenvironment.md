---
title: '&lt;serviceHostingEnvironment&gt;'
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: e6c69e06b691e40b6b2c39a54be83d7bdbe3a650
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicehostingenvironmentgt"></a>&lt;serviceHostingEnvironment&gt;
Este elemento define o tipo que o ambiente de hospedagem de serviço instancia para um transporte particular. Se esse elemento estiver vazio, o tipo padrão é usado. Esse elemento só pode ser usado no aplicativo ou arquivos de configuração no nível de máquina.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean" 
                           minFreeMemoryPercentageToActivateService="Integer" 
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String" service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String" transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|aspNetCompatibilityEnabled|Um valor booliano que indica se o modo de compatibilidade ASP.NET foi ativado para o aplicativo atual. O padrão é `false`.<br /><br /> Quando esse atributo é definido como `true`, fluem de solicitações para serviços do Windows Communication Foundation (WCF) por meio do pipeline HTTP do ASP.NET e comunicação por meio de protocolos não HTTP está proibida. Para obter mais informações, consulte [serviços WCF e ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).|  
|minFreeMemoryPercentageToActivateService|Um inteiro que especifica a quantidade mínima de memória livre que deve estar disponível para o sistema, antes que um serviço [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] possa ser ativado. **Cuidado:** especificar esse atributo juntamente com confiança parcial no arquivo Web. config de um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviço resultará em um <xref:System.Security.SecurityException> quando o serviço é executado.|  
|multipleSiteBindingsEnabled|Um valor booleano que especifica se várias associações IIS por site está habilitado.<br /><br /> IIS consiste em sites, que são contêineres de aplicativos virtuais que contém diretórios virtuais. O aplicativo em um site pode ser acessado por meio de um ou mais associação do IIS. Uma associação IIS oferece dois tipos de informações: um protocolo de associação e informações de associação. Protocolo de associação define o esquema durante o qual a comunicação ocorre, e informações de associação são as informações usadas para acessar o site. Um exemplo de um protocolo de associação pode ser HTTP, enquanto as informações de associação podem conter um endereço IP, porta, o cabeçalho de host, etc.<br /><br /> O IIS oferece suporte à especificação várias associações IIS por site, o que resulta em vários endereços de base por esquema. No entanto, um serviço do Windows Communication Foundation (WCF) hospedado em um site permite que a associação baseAddress apenas uma por esquema.<br /><br /> Para habilitar várias associações IIS por site para um serviço do Windows Communication Foundation (WCF), defina este atributo como `true`. Observe que várias associação de site só tem suporte para o protocolo HTTP. O endereço dos pontos de extremidade no arquivo de configuração deve ser um URI completo.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|Uma coleção de elementos de configuração que especificam filtros de prefixo para os endereços base usados pelo host de serviço.|  
|[\<serviceActivations >](../../../../../docs/framework/configure-apps/file-schema/wcf/serviceactivations.md)|Uma seção de configuração que descreve as configurações de ativação.|  
|[\<transportConfigurationTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/transportconfigurationtypes.md)|Uma coleção de elementos de configuração que identificam o tipo de um transporte particular.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|ServiceModel|O elemento raiz de todos os elementos de configuração do Windows Communication Foundation (WCF).|  
  
## <a name="remarks"></a>Comentários  
 Por padrão, os serviços de WCF para execução lado a lado com o ASP.NET em domínios de aplicativo hospedado (AppDomain). Embora o WCF e ASP.NET podem coexistir no mesmo AppDomain, solicitações WCF não serão processadas pelo Pipeline de HTTP do ASP.NET por padrão. Como resultado, vários elementos da plataforma do aplicativo ASP.NET não estão disponíveis para os serviços WCF. Esses incluem  
  
-   Autorização de URL da arquivo ASP.NET  
  
-   Representação do ASP.NET  
  
-   Estado da sessão baseada em cookie  
  
-   HttpContext  
  
-   Extensibilidade de pipeline por meio de HttpModule personalizado  
  
 Se precisam de seus serviços WCF funcionar no contexto do ASP.NET e se comunicar somente por HTTP, você pode usar o modo de compatibilidade do ASP.NET do WCF. Esse modo é ativado quando o `aspNetCompatibilityEnabled` atributo é definido como `true` no nível do aplicativo. Implementações de serviço devem declarar a capacidade de executar em modo de compatibilidade usando o <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> classe. Quando o modo de compatibilidade é habilitado,  
  
-   Autorização de URL da arquivo ASP.NET é aplicada antes de autorização do WCF. Uma decisão de autorização baseia-se a identidade de nível de transporte da solicitação. Identidades no nível da mensagem são ignoradas.  
  
-   Operações de serviço WCF começam a executar no contexto de representação do ASP.NET. Se a representação do WCF e representação do ASP.NET estão habilitados para um serviço específico, o contexto de representação do WCF se aplica.  
  
-   HttpContext pode ser usado no código de serviço do WCF e serviços são impedidos de expor pontos de extremidade HTTP não.  
  
-   WCF são processadas pelo pipeline do ASP.NET. HttpModules que foram configurados para atuar em solicitações de entrada também pode processar solicitações WCF. Isso inclui componentes de plataforma do ASP.NET (por exemplo, <xref:System.Web.SessionState.SessionStateModule>), bem como módulos personalizados de terceiros.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra como habilitar o modo de compatibilidade do ASP.  
  
## <a name="code"></a>Código  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [Hospedagem](../../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Serviços do WCF e ASP.NET](../../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
